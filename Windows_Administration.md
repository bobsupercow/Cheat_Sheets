### SysInternals Tools ###

For access to all of the sysinternals tools on any Windows box with internet, just Win+R and open 
`\\live.sysinternals.com@SSL@443\tools`



## Enable Administrative Shares on Windows 10 ##

[Source](https://tommynation.com/enable-remote-access-administrative-shares-windows-10/)

### The issue: ###
Adminstrative shares are default shares of all the disk drives on a Windows computer. These allow access to the root disks remotely.

If you try to connect to adminstrative shares (for instance C$ or D$) on a remote computer running a newer version of Windows than Windows XP, you will not be able to.

### The solution: ###
 * Using a local administrator account, enable Advanced Sharing. 
 * Right-click any disk drive using File Explorer and click “Properties”. Then click “Advanced Sharing” and turn on file sharing when it asks if you want to enable it. (Don’t share the disk drive, just close the dialog box.)

At this point, you can connect to a remote share (i.e \\SERVERNAME\c$) but get prompted to enter a username and password and even with the correct credentials it will error out. 
This is because of a default security policy that disables access to adminstrative shares.

### Registry Fix ###

1. Click the Windows Start icon and search for “regedit”. Right-click and select “run as administrator”.
1. Expand the tree to HKEY_LOCAL_MACHINE \ SOFTWARE \ Microsoft\ Windows \ CurrentVersion \ policies \ system.
1. Create a new key (Right click -> New -> choose “DWORD Value (32bit)”).
1. Name the key “LocalAccountTokenFilterPolicy” and give it the value of “1”. Click OK.
1. Reboot the server to enable the setting to take effect.
