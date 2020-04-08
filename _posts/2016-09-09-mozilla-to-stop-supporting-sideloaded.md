---
title: 'Mozilla to stop supporting sideloaded extensions in Firefox'
date: 2019-11-01T02:26:00+01:00
draft: false
---

![firefox.png](https://zdnet2.cbsistatic.com/hub/i/2019/11/01/a4fb8186-b7f3-4e61-8a77-16050e1b1fb6/132c3d218a38cf3ebaa1a37ef70052de/firefox.png)

Image: Mozilla

Mozilla has announced today plans to discontinue one of the three methods through which extensions can be installed in Firefox.

Starting next year, Firefox users won't be able to install extensions by placing an XPI extension file inside a special folder inside a user's Firefox directory.

[The method](https://extensionworkshop.com/documentation/publish/distribute-sideloading/#standard-extension-folders), known as sideloading, was initially created to aid developers of desktop apps. In case they wanted to distribute a Firefox extension with their desktop app, the developers could configure the app's installer to drop a Firefox XPI extension file inside the Firefox browser's folder.

### Sideloading removed because of abuse

This method has been available to Firefox extension developers since the browser's early days. However, today, Mozilla announced plans to discontinue supporting sideloaded extensions, citing security risks.

"Sideloaded extensions frequently cause issues for users since they did not explicitly choose to install them and are unable to remove them from the Add-ons Manager," said Caitlin Neiman, Add-ons Community Manager at Mozilla.

"This mechanism has also been employed in the past to install malware into Firefox," Neiman said.

### Two-phase removal plan

As a result, Mozilla plans to stop supporting this feature next year in a two-phase plan.

The first will take place with the release of Firefox 73 in February 2020. Neiman says Firefox will continue to read sideloaded extensions, but they'll be slowly converted into normal add-ons inside a user's Firefox profile, and made available in the browser's Add-ons section.

By March 2020, with the release of Firefox 74, Mozilla plans to completely remove the ability to sideload an extension. By that point, Mozilla hopes that all sideloaded extensions will be moved inside users' Add-ons section.

Through the move, Mozilla also hopes to help clean up some Firefox installations where malware authors were secretly sideloading extensions behind users' backs. Since these extensions will now show up in the Add-ons sections, users will be able to remove any extensions they don't need or don't remember installing.

### Two methods of loading extensions remain

Further, [Mozilla's blog post](https://blog.mozilla.org/addons/2019/10/31/firefox-to-discontinue-sideloaded-extensions/) on the matter today also serves as a notice for extension developers, who will have to update their extensions and make them available through another installation mechanism.

There are currently two other ways through which developers can distribute extensions, and through which users can install them.

The first and the most widely known is by installing extensions from the official [addons.mozilla.org](https://addons.mozilla.org/en-US/firefox/) (AMO) portal. Extensions listed here are verified by Mozilla, so most are relatively safe, albeit the security checks aren't 100% sure to catch all malicious code.

The second involves using the "[Install Add-on From File](https://extensionworkshop.com/documentation/publish/distribute-sideloading/)" option in Firefox's Add-ons section. Users have to manually download a Firefox XPI extension file, visit the Add-ons section, and then use the "Install Add-on From File" option to load the extension in their browser. This option is usually employed for loading extensions that have to handle sensitive corporate data inside enterprise environments, and can't be distributed via the AMO portal.

There was also [a fourth method](https://extensionworkshop.com/documentation/enterprise/enterprise-distribution/#installation-using-windows-registry) of loading extensions inside Firefox, but this was removed in September 2018, with the release of Firefox 62. This involved modifying Windows Registry keys to load custom extensions with Firefox installations. This, too, was abused by malware devs, and Mozilla decided to remove it.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2BYiPwP