## Copying Files

### Copy with robocopy keeping permissions, and directory structure, log to file ###

    robocopy.exe \sourcepath \target-path /MIR /xo /xj /dcopy:t /copy:datso /secfix /v /FP /MT /e /z /r:0 /w:0 /log+:c:\temp\logfile.log /b /zb
