# VPN


## Permissions

First of all, you need to get the permissions.

Email Mathias Bothe (Mathias.Bothe@eawag.ch) attaching the form in this directory (`VPN_form.pdf`) that I am attaching to this email.
Use your eawag account and put your group leader in cc:.

## Installation

Connect to the intranet, internal.eawag.ch, and type vpn in the search engine. Otherwise, just open this file, which contains the instructions:
https://webvpn.eawag.ch/https/www.internal.eawag.ch/fileadmin_intranet/intranet/informatik/komm_kanaele/extern/pa_global_protect_winmac_e.pdf

If you are not at Eawag, you can still access the intranet by logging into https://webvpn.eawag.ch/global-protect/portal/portal.esp

If you have **mac** or **windows**, you simply download the VPN program from vpn.eawag.ch, and follow the instructions.

If you have **linux**, the program is hidden (wtf!) at this path:
https://www.eawag.ch/repository/pa_gp_client/

and you can find the instructions here.
https://www.eawag.ch/repository/pa_gp_client/5.1.1/globalprotect-app-user-guide.pdf


Further documentation: 

https://docs.paloaltonetworks.com/globalprotect/5-1/globalprotect-app-user-guide/globalprotect-app-for-linux/download-and-install-the-globalprotect-app-for-linux.html 

https://docs.paloaltonetworks.com/globalprotect/5-1/globalprotect-app-user-guide/globalprotect-app-for-linux/use-the-globalprotect-app-for-linux.html



## Executing

Usually, a small icon will appear on your main toolbar, and you will use it for the 2-factor authentication. Otherwise, if you want to run from terminal, you can use one of the following options:


##### Run from the globalprotect shell
You first launch `globalprotect`, and from the shell you type `connect -portal vpn.eawag.ch`:
```
user@machine:~$ globalprotect
Current GlobalProtect status: OnDemand mode.                           
>> connect -portal vpn.eawag.ch
Retrieving configuration...                                            
vpn.eawag.ch - Enter login credentials
username(baccimar):baccimar  
Password:
Discovering network...                                                 
Enter Your Microsoft verification code:                                
Connecting...                                                          
Connected
```

##### Launch the GUI
You type `globalprotect launch-ui` in your terminal, and the GUI opens, with the 2-factor authentication.

