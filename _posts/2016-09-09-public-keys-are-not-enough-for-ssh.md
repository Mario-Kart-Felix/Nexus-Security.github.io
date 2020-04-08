---
title: 'Public keys are not enough for SSH security'
date: 2019-10-27T07:02:00+01:00
draft: false
---

If your organization uses SSH public keys, it’s entirely possible you have already mislaid one. There is a file sitting in a backup or on a former employee’s computer which grants the holder access to your infrastructure. If you share SSH keys between employees it’s likely only a few keys are enough to give an attacker access to your entire system. If you don’t share them, it’s likely your team has generated so many keys you long lost track of at least one.

If an attacker can breach a single one of your client devices it’s likely there is a `known_hosts` file which lists every target which can be trivially reached with the keys the machine already contains. If someone is able to compromise a team member’s laptop, they could use keys on the device that lack password protection to reach sensitive destinations.

Should that happen, how would you respond and revoke the lost SSH key? Do you have an accounting of the keys which have been generated? Do you rotate SSH keys? How do you manage that across an entire organization so consumed with serving customers that security has to be effortless to be adopted?

Cloudflare Access [launched](https://blog.cloudflare.com/releasing-the-cloudflare-access-feature-that-let-us-smash-a-vpn-on-stage/) support for SSH connections last year to bring zero-trust security to how teams connect to infrastructure. Access integrates with your IdP to bring SSO security to SSH connections by enforcing identity-based rules each time a user attempts to connect to a target resource.

However, once Access connected users to the server they still had to rely on legacy SSH keys to authorize their account. Starting today, we’re excited to help teams remove that requirement and replace static SSH keys with short-lived certificates.

Replacing a private network with Cloudflare Access
--------------------------------------------------

In traditional network perimeter models, teams secure their infrastructure with two gates: a private network and SSH keys.

The private network requires that any user attempting to connect to a server must be on the same network, or a peered equivalent (such as a VPN). However, that introduces some risk. Private networks default to trust that a user on the network can reach a machine. Administrators must proactively segment the network or secure each piece of the infrastructure with control lists to work backwards from that default.

Cloudflare Access secures infrastructure by starting from the other direction: no user should be trusted. Instead, users must prove they should be able to access any unique machine or destination by default.

We released support for SSH connections in Cloudflare Access [last year](https://blog.cloudflare.com/releasing-the-cloudflare-access-feature-that-let-us-smash-a-vpn-on-stage/) to help teams leave that network perimeter model and replace it with one that evaluates every request to a server for user identity. Through integration with popular identity providers, that solution also gives teams the ability to bring their SSO pipeline into their SSH flow.

Replacing static SSH keys with short-lived certificates
-------------------------------------------------------

Once a user is connected to a server over SSH, they typically need to authorize their session. The machine they are attempting to reach will have a set of profiles which consists of user or role identities. Those profiles define what actions the user is able to take.

SSH processes make a few options available for the user to login to a profile. In some cases, users can login with a username and password combination. However, most teams rely on public-private key certificates to handle that login. To use that flow, administrators and users need to take prerequisite steps.

Prior to the connection, the user will generate a certificate and provide the public key to an administrator, who will then configure the server to trust the certificate and associate it with a certain user and set of permissions. The user stores that certificate on their device and presents it during that last mile. However, this leaves open all of the problems that SSO attempts to solve:  

*   Most teams never force users to rotate certificates. If they do, it might be required once a year at most. This leaves static credentials to core infrastructure lingering on hundreds or thousands of devices.
*   Users are responsible for securing their certificates on their devices. Users are also responsible for passwords, but organizations can enforce requirements and revocation centrally.
*   Revocation is difficult. Teams must administer a CRL or OCSP platform to ensure that lost or stolen certificates are not used.

With Cloudflare Access, you can bring your SSO accounts to user authentication within your infrastructure. No static keys required.

How does it work?
-----------------

To build this we turned to three tools we already had: Cloudflare Access, Argo Tunnel and Workers.

Access is a policy engine which combines the employee data in your identity provider (like Okta or AzureAD) with policies you craft. Based on those policies Access is able to limit access to your internal applications to the users you choose. It’s not a far leap to see how the same policy concept could be used to control access to a server over SSH. You write a policy and we use it to decide which of your employees should be able to access which resources. Then we generate a short-lived certificate allowing them to access that resource for only the briefest period of time. If you remove a user from your IdP, their access to your infrastructure is similarly removed, seamlessly.

To actually funnel the traffic through our network we use another existing Cloudflare tool: Argo Tunnel. Argo Tunnel flips the traditional model of connecting a server to the Internet. When you spin up our daemon on a machine it makes outbound connections to Cloudflare, and all of your traffic then flows over those connections. This allows the machine to be a part of Cloudflare’s network without you having to expose the machine to the Internet directly.

For HTTP use cases, Argo Tunnel only needs to run on the server. In the case of the Access SSH flow, we proxy SSH traffic through Cloudflare by running the Argo Tunnel client, `cloudflared`, on both the server and the end user’s laptop.

When users connect over SSH to a resource secured by Access for Infrastructure, they use the command-line tool `cloudflared`. `cloudflared` takes the SSH traffic bound for that hostname and forwards it through Cloudflare based on SSH config settings. No piping or command wrapping required. `cloudflared` launches a browser window and prompts the user to authenticate with their SSO credentials.

Once authenticated, Access checks the user's identity against the policy you have configured for that application. If the user is permitted to reach the resource, Access generates a JSON Web Token (JWT), signed by Cloudflare and scoped to the user and application. Access distributes that token to the user’s device through `cloudflared` and the tool stores it locally.

Like the core Access authentication flow, the token validation is built with a Cloudflare Worker running in every one of our data centers, making it both fast and highly available. Workers made it possible for us to deploy this SSH proxying to all 194 of Cloudflare’s data centers, meaning Access for Infrastructure often speeds up SSH sessions rather than slowing them down.

![](https://blog-cloudflare-com-assets.storage.googleapis.com/2019/10/Short-lived-Cert-copy@2x-1.png)

With short-lived certificates enabled, the instance of `cloudflared` running on the client takes one additional step. `cloudflared` sends that token to a Cloudflare certificate signing endpoint that creates an ephemeral certificate. The user's SSH flow then sends both the token, which is used to authenticate through Access, and the short-lived certificate, which is used to authenticate to the server. Like the core Access authentication flow, the token validation is built with a Cloudflare Worker running in every one of our data centers, making it both fast and highly available.

![](https://blog-cloudflare-com-assets.storage.googleapis.com/2019/10/Short-lived-Cert@2x.png)

When the server receives the request, it validates the short-lived certificate against that public key and, if authentic, authorizes the user identity to a matching Unix user. The certificate, once issued, is valid for 2 minutes but the SSH connection can last longer once the session has started.

What is the end user experience?
--------------------------------

Cloudflare Access’ SSH feature is entirely transparent to the end user and does not require any unique SSH commands, wrappers, or flags. Instead, Access requires that your team members take a couple one-time steps to get started:

#### 1\. Install the cloudflared daemon

The same lightweight software that runs on the target server is used to proxy SSH connections from your team members’ devices through Cloudflare. Users can install it with popular package managers like brew or at the link available [here](https://developers.cloudflare.com/access/cli/installing-cli-tool/). Alternatively, the software is open-source and can be built and distributed by your administrators.

#### 2\. Print SSH configuration update and save

Once an end user has installed `cloudflared`, they need to run one command to generate new lines to add to their SSH config file:

```
cloudflared access ssh-config --hostname vm.example.com --short-lived-cert
```

The `--hostname` field will contain the hostname or wildcard subdomain of the resource protected behind Access. Once run, `cloudflared` will print the following configurations details:

```
Host vm.example.com ProxyCommand bash -c '/usr/local/bin/cloudflared access ssh-gen --hostname %h; ssh -tt %[[email protected]](https://blog.cloudflare.com/cdn-cgi/l/email-protection) >&2 <&1' Host cfpipe-vm.example.com HostName vm.example.com ProxyCommand /usr/local/bin/cloudflared access ssh --hostname %h IdentityFile ~/.cloudflared/vm.example.com-cf_key CertificateFile ~/.cloudflared/vm.example.com-cf_key-cert.pup
```

Users need to append that output to their SSH config file. Once saved, they can connect over SSH to the protected resource. Access will prompt them to authenticate with their SSO credentials in the browser, in the same way they login to any other browser-based tool. If they already have an active browser session with their credentials, they’ll just see a success page.

In their terminal, `cloudflared` will establish the session and issue the client certificate that corresponds to their identity.

What’s next?
------------

With short-lived certificates, Access can become a single SSO-integrated gateway for your team and infrastructure in any environment. Users can SSH directly to a given machine and administrators can replace their jumphosts altogether, removing that overhead. The feature is available today for all Access customers. You can get started by following the documentation available [here](https://developers.cloudflare.com/access/ssh/short-live-cert-server/).

  
  
from Hacker News https://ift.tt/2BGN1wi