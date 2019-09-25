## Copying Files

[Source](https://www.reddit.com/r/sysadmin/comments/aw5f5l/whats_your_goto_copy_command_for_large_amounts_of/)
### Step 1 - Initial copy of the data ###

    `robocopy \\OLDSERVER\d$\FOLDER D:\FOLDER /e /zb /copy:DATSOU /r:3 /w:3 /log:c:\ROBOCOPY-Logs\FOLDER.log /V /NP

* OLDSERVER is the source fileserver
* D$ is the drive letter on the Source Server
* D is the drive letter on the new server.

* /E Copy subdirectories recursively, (including empty ones.)
* /ZB Use ‘restartable’ mode, and if this fails use ‘backup’ mode.
* /copy:DATSOU Copy Data, Attributes, Time Stamps, Security, Owner, aUditing information
* /R:3 Retry three times, if you don’t specify this, it will retry one million times!
* /W:3 Wait time between the retries above.
* /log Will output the log to the folder we created above.
* /V Produce output in verbose (detailed) mode.
* /NP Do not show percentage progress
