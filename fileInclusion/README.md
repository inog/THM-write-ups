# File Inclusion 
## This room introduces file inclusion vulnerabilities, including Local File Inclusion (LFI), Remote File Inclusion (RFI), and directory traversal.

My notes and write ups to the room inclusion on TryHackMe
https://tryhackme.com/room/fileinc


Path traversal attacks -> dot-dot-slash attacks  (../)
../../ until root and then go to the interessting files.  

i.e. 
http://webapp.thm/get.php?file=../../../../boot.ini  
http://webapp.thm/get.php?file=../../../../windows/win.ini  

|Location	            |Description      |
|---------------------------|-----------------| 
|/etc/issue	            |contains a message or system identification to be printed before the login prompt.|
|/etc/profile	            |controls system-wide default variables, such as Export variables, File creation mask (umask), Terminal types, Mail messages to indicate when new mail has arrived|
|/proc/version	            |specifies the version of the Linux kernel|
|/etc/passwd	            |has all registered user that has access to a system|
|/etc/shadow	            |contains information about the system's users' passwords|
|/root/.bash_history        |contains the history commands for root user|
|/var/log/dmessage          |contains global system messages, including the messages that are logged during system startup|
|/var/mail/root             |all emails for root user|
|/root/.ssh/id_rsa          |Private SSH keys for a root or any known valid user on the server|
|/var/log/apache2/access.log|the accessed requests for Apache  webserver|
|C:\boot.ini|contains the boot options for computers with BIOS firmware|

### Task 5 

NullByte `%00`
<Using null bytes is an injection technique where URL-encoded representation such as %00 or 0x00 in hex with user-supplied data to terminate strings. You could think of it as trying to trick the web app into disregarding whatever comes after the Null Byte.

By adding the Null Byte at the end of the payload, we tell the  include function to ignore anything after the null byte which may look like:

include("languages/../../../../../etc/passwd%00").".php"); which equivalent to → include("languages/../../../../../etc/passwd");


