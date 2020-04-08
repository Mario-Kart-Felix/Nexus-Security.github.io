---
title: 'RedPeanut'
date: 2019-11-30T22:49:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-sCHsb1ETSH4/XdAnJ_y_xBI/AAAAAAAAQ20/6sF0TaNXO7sZLAJtBO-OV9pQ162wI2mAACNcBGAsYHQ/s640/rat.jpg)](https://1.bp.blogspot.com/-sCHsb1ETSH4/XdAnJ_y_xBI/AAAAAAAAQ20/6sF0TaNXO7sZLAJtBO-OV9pQ162wI2mAACNcBGAsYHQ/s1600/rat.jpg)

**RedPeanut - A Small RAT Developed In .Net Core 2 And Its Agent In .Net 3.5/4.0**

  

  

  
RedPeanut is a small RAT developed in .Net Core 2 and its agent in .Net 3.5 / 4.0. RedPeanut code execution is based on shellcode generated with[DonutCS](https://github.com/n1xbyte/donutCS "DonutCS"). It is therefore a hybrid, although developed in .Net it does not rely solely on the Assembly.Load. This increases the detection surface, but allows us to practice and experiment with various evasion techniques related to the dotnet environment, process management and injection. This behavior can be changed at rutime with the "managed" and "unmanaged" commands. If you are interested in a .Net[C2 Framework](https://www.kitploit.com/search/label/C2%20Framework "C2 Framework")that is consistent and can be used in an enagement, I suggest[Covenant](https://github.com/cobbr/Covenant "Covenant").  
[

](https://www.blogger.com/u/1/null)  
RedPeanut is weaponized with:  

*   GhostPack
*   SharpGPOAbuse
*   SharpCOM
*   EvilClippy
*   DotNetToJS
*   SharpWeb
*   Modified version of PsExec
*   SharpSploit
*   TikiTorch

  
**RedPeanut Agent**  
The RedPeanut agent can be compiled in .Net 3.5 and 4.0 and has pivoting capabilities via NamedPipe. The agent, when executed in an unmanaged mode, performs its own critical tasks in a separate process to prevent the AV response to detection or error during execution make you lose the whole agent.  
The execution flow is as follow:  

1.  Process creation
2.  Inject static shellcode generated with DonutCS
3.  The loader loads and executes the stager or module

The agent currently only supports https channel.  
  
**C2 Channel**  
The agent checkin protocol is very simple:  

1.  The stager requires an agent id, the message is encrypted with RC4 with the shared serverkey
2.  The server decrypt the message, compile and sends the agent, generate and send KEY and IV for future communications AES encryption, the message is encrypted RC4
3.  The stager decrypt the message and load the agent via Assembly.Load
4.  The agent sends a checkin message to the server, the message is encrypted with AES

Alternatively, the covered channel feature can be activated(at the moment it is just a PoC). The idea is to imitate the web traffic carried out by a real user. Usually a web page is composed of the html page and all the objects necessary for its display as css, images, etc. At the request of a new task the answer from the server will not be directly the encrypted task but an html page from which to extract the link to the image that will have embedded the encrypted task. The http request for the image will contain the Referer header.  
  
**Content delivery**  
Content delivery is organized in 4 channels:  

1.  C2 Channe customizable via profile
2.  Dynamic content generated/managed by RedPeanut customizable via profile
3.  Static content mapped to /file/
4.  Covered channel for the recovery of the image containing the payload mapped to /images/

  
**Profiles**  
RedPeanut capability of customization of network[footprint](https://www.kitploit.com/search/label/Footprint "footprint")both server side and client side. The properties that can be set are:  

*   _General_
    *   Delay (between requests)
    *   ContentUri (url of dynamic content eg. dll hta etc.)
    *   UserAgent
    *   Spawn (the process to create to perform critical tasks)
    *   HtmlCovered (Enable covered channel)
    *   TargetClass (Class to search for image recover)
*   _Http Get_
    *   ApiPath (comma separated list of url es /news-list.jsp,/antani.php etc.)
    *   _Server_
        *   Prepend
        *   Append
        *   Headers (name and value pair for http headers)
    *   _Client_
        *   Headers    
*   _Http Post_
    *   ApiPath (comma separated list of url es /news-list.jsp,/antani.php etc.)
    *   Param (the name of the post request payload parameter)
    *   Mask (format for interpreting the key value pair eg {0}={1}) (need more work...)
    *   _Server_
        *   Prepend
        *   Append
        *   Headers (name and value pair for http headers)
    *   _Client_
        *   Headers

_Domain Fronting_  
To enable the[domain fronting](https://www.kitploit.com/search/label/Domain%20Fronting "domain fronting")support it is necessary to value the "Host" header in the client section, both post and get (exemplified in the default profile 2)  
  
**PowerShellExecuter**  
The PowerShellExecuter module allows you to execute oneliner commands or files in a runspace with AMSI bypass, Logging bypass and[PowerView](https://www.kitploit.com/search/label/PowerView "PowerView")already loaded.  
  
**Launchers**  

*   Exe
*   Dll
*   PowerShell
*   Hta (vbs,powershell)
*   InstallUtil
*   MSBuild
*   MacroVba

  
**Local modules**  

*   EvilClippy

  
**Agent Tasks**  

*   Upload
*   DownLoad
*   SharpWeb
*   SharpWmi
*   SharpUp
*   UACBypass Token Duplication
*   SharpDPAPIVaults
*   SharpDPAPITriage
*   SharpDPAPIRdg
*   SharpDPAPIMasterKeys
*   SharpDPAPIMachineVaults
*   SharpDPAPIMachineTriage
*   SharpDPAPIMachineMasterKeys
*   SharpDPAPIMachineCredentials
*   SharpDPAPICredentials
*   SharpDPAPIBackupKey
*   Seatbelt
*   SafetyKatz
*   RubeusTriage
*   RubeusTgtDeleg
*   RubeusS4U
*   RubeusRenew
*   RubeusPurge
*   RubeusPtt
*   RubeusMonitor
*   RubeusKlist
*   RubeusKerberoast
*   RubeusHash
*   RubeusHarvest
*   RubeusDump
*   RubeusDescribe
*   RubeusCreateNetOnly
*   RubeusChangePw
*   RubeusASREPRoast
*   RubeusAskTgt
*   SharpCOM
*   SharpGPOAddUserRights
*   SharpGPOAddStartupScript
*   SharpGPOAddLocalAdmin
*   SharpGPOAddImmediateTask
*   PowerShellExecuter
*   LatteralMSBuild
*   SharpPsExec
*   SharpAdidnsdump
*   PPIDAgent
*   SpawnAsAgent
*   SpawnShellcode
*   SpawnAsShellcode
*   SharpMiniDump

  
**Persistence**  

*   Autorun
*   Startup
*   WMI
*   CRL

  
**BlockDlls**  
Starting with version 0.3.0 RedPeanutAgent supports the blockdlls command. With this option enabled, child processes that are created to perform tasks in unmanaged mode are created with the attribute PROCESS\_CREATION\_MITIGATION\_POLICY\_BLOCK\_NON\_MICROSOFT\_BINARIES\_ALWAYS\_ON. This attribute prevents the process of loading dlls that are not signed by Microsoft, this could protect our tasks from AV and EDR hooking techniques.  
  
**Direct Sysstem Call and Dynamic Dll Loading**  
RedPeanutAgent uses Dynamic Dll loading to avoiding using of suspicious Dll Imports. Credits for Dynamic Dll Loading goes to[@TheRealWover](https://twitter.com/TheRealWover "@TheRealWover"),[@cobbr\_io](https://twitter.com/cobbr_io "@cobbr_io")and[@FuzzySec](https://twitter.com/FuzzySec "@FuzzySec")for their work in[SharpSploit](https://github.com/cobbr/SharpSploit/tree/master/SharpSploit/Execution/DynamicInvoke "SharpSploit").  
Some AV and EDR vendors used hooking technique to keep track of activities. To avoid using hooked syscall RedPeanutAgent uses direct syscall, auto injecting the necessary code. Credits for Direct Syscall goes to[@Cneelis](https://github.com/outflanknl/Dumpert "@Cneelis")  
  
**Running**  
To run RedPeanut you need to have dotnet installed. To install dotnet on Kali:  
```
wget -qO- [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc) | gpg --dearmor > microsoft.asc.gpg  
mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/  
wget -q [https://packages.microsoft.com/config/debian/9/prod.list](https://packages.microsoft.com/config/debian/9/prod.list)  
mv prod.list /etc/apt/sources.list.d/microsoft-prod.list  
chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg  
chown root:root /etc/apt/sources.list.d/microsoft-prod.list  
  
apt-get install apt-transport-https  
apt-get update  
apt-get install dotnet-sdk-2.1
``````
git clone --recursive [https://github.com/b4rtik/RedPeanut.git](https://github.com/b4rtik/RedPeanut.git)
```For the covered channel functionality it is necessary to install the libgdiplus library, therefore:  
For linux users:  
```
apt-get install -y libgdiplus
```For OSx  
```
brew install mono-libgdiplus
```Assembly signing key generation  
```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community>sn.exe -k 4096 key.snk
```Than copy key.snk in Workspace/KeyFile  
```
root@kali:~# cd RedPanut  
root@kali:~/RedPeanut# dotnet run  
Using launch settings from /root/Projects/RedPeanut/Properties/launchSettings.json...  
Enter password to encrypt serverkey:   
  
__________________________________________________________________________  
ooooooo________________oo_ooooooo___________________________________oo____  
oo____oo___ooooo___oooooo_oo____oo__ooooo___ooooo__oo_ooo__oo____o__oo____  
oo____oo__oo____o_oo___oo_oo____oo_oo____o_oo___oo_ooo___o_oo____o_oooo___  
ooooooo___ooooooo_oo___oo_oooooo___ooooooo_oo___oo_oo____o_oo____o__oo____  
oo____oo__oo______oo___oo_oo_______oo______oo___oo_oo____o_ooo___o__oo__o_  
oo_____oo__ooooo___oooooo_oo________ooooo___oooo_o_oo____o_oo_ooo____ooo__  
__________________________________________________________________________  
________________________________________________RedPeanut_v0.3.0___@b4rtik  
________________________________________________________________________   __  
  
[*] No profile avalilable, creating new one...  
[RP] >
```  
**Shellcode generator**  
[DonutCS](https://github.com/n1xbyte/donutCS "DonutCS")is a shellcode generation tool that creates position-independant shellcode payloads from .NET Assemblies. This shellcode may be used to inject the Assembly into arbitrary Windows processes. Given an arbitrary .NET Assembly, parameters, and an entry point (such as Program.Main), it produces position-independent shellcode that loads it from memory. The .NET Assembly can either be staged from a URL or stageless by being embedded directly in the shellcode.  
  
**CLR Persistence**  
The CLR persistence technique was presented for the first time in this[post](https://www.contextis.com/en/blog/common-language-runtime-hook-for-persistence "post")by[@Am0nsec](https://twitter.com/am0nsec "@Am0nsec"). The technique consists in carrying out the application domain manager hooking. As described in the post, the assembly to carry out hooking is necessary which is available in the GAC. An assembly to be used from the GAC must be strong-named and then signed with a key. The CLR persistence module needs a key to be able to sign the assemblies, which can be generated with the sn.exe tool as follows:  
```
**********************************************************************  
** Visual Studio 2017 Developer Command Prompt v15.9.3  
** Copyright (c) 2017 [Microsoft](https://www.kitploit.com/search/label/Microsoft "Microsoft") Corporation  
**********************************************************************  
  
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community>sn.exe -k 4096 key.snk
```Copy the key.snk file to Workspace/KeyFile folder. This file will be used to sign the assembly for persistence.  
  
**Tools updating**  
Some of the well-known tools present in RedPeanut such as the GhostPack tools are wrapped in full and executed on the client side. To update the tools, for example SeatBelt, without updating the entire repository is necessary: Clone the Seatbelt repository, rename the "Main" method in "Execute", insert the public modifier and recompile as dll. The dll must be compressed and encoded in Base64 with the ps RastaMouse's script[Get-CompressedShellcode.ps1](https://github.com/rasta-mouse/TikiTorch/blob/dev/Get-CompressedShellcode.ps1 "Get-CompressedShellcode.ps1")  
  
**Credits**  

*   Donut -[@TheRealWover](https://twitter.com/TheRealWover "@TheRealWover")
*   DonutCS -[@n1xbyte](https://github.com/n1xbyte/donutCS "@n1xbyte")
*   SharpSploit -[@cobbr\_io](https://twitter.com/cobbr_io "@cobbr_io")
*   GhostPack -[@harmj0y](https://twitter.com/harmj0y "@harmj0y")
*   SharpCOM -[@rvrsh3ll](https://twitter.com/424f424f "@rvrsh3ll")
*   SharpGPOAbuse -[@mwrlabs](https://twitter.com/mwrlabs "@mwrlabs")
*   EvilClippy -[@StanHacked](https://twitter.com/StanHacked "@StanHacked")
*   DotNetToJS -[@tiraniddo](https://twitter.com/tiraniddo "@tiraniddo")
*   Sharpshooter -[@domchell](https://twitter.com/domchell "@domchell")
*   SharpWeb -[@djhohnstein](https://twitter.com/djhohnstein "@djhohnstein")
*   Original version of PsExec -[@malcomvetter](https://twitter.com/malcomvetter "@malcomvetter")
*   TikiTorch -[@\_RastaMouse](https://twitter.com/_RastaMouse "@_RastaMouse")
*   ReadLine -[Toni Solarin-Sodara](https://github.com/tonerdo/readline "Toni Solarin-Sodara")

  
  

**[Download RedPeanut](http://hopigrarn.com/3lwi "Download RedPeanut")**

**  
Regards**

**Kang Asu**