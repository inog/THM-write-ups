# TryHackMe: room: *injection*

This is my write up for the room injection at [TryHackMe:injection]( https://tryhackme.com/room/injection)

## Task 1 
- read the intro stuff
- start the machine an go ahead

## Task 2
read about *What is OS Command Injection*

## Task 3

### Blind Command Injection

At this task we have to navigate to an Url which is the IP from the started Machine. 

If you not using vpn to connnect to the machine you have to start the Attackbox.  
In the attackbox open firefox and navigate to the suggested link. 
Here you can try out the described commands. 

open the terminal and try to ping the given server.
use `ping -h` to check the help page. 

#### Ping the box with 10 packets. What is this command (without IP address)?
`ping -c 10 <IP-Address>`

#### Redirect the box's Linux Kernel Version to a file on the web server.  What is the Linux Kernel Version?
First of all you have to know how the Linux version is displayed to the terminal.
This website could help. https://linuxize.com/post/how-to-check-the-kernel-version-in-linux/

after that you can use the `>` to foward the output into a file.



#### Enter "root" into the input and review the alert.  What type of alert do you get?
the answer is `Success'

#### Enter "www-data" into the input and review the alert.  What type of alert do you get?
the answer is `Success'

#### Enter your name into the input and review the alert.  What type of alert do you get?
the answer is `Success'



