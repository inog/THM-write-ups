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
try the following  
`a;whoami > w.txt` and go with the browser to `<IP>/w.txt`  
To solve this question paste the following into the inputbox:   
`a; uname -r > kernel.txt` go to website `<IP>/kernel.txt`


#### Enter "root" into the input and review the alert.  What type of alert do you get?
the answer is `Success`

#### Enter "www-data" into the input and review the alert.  What type of alert do you get?
the answer is `Success`

#### Enter your name into the input and review the alert.  What type of alert do you get?
the answer is `Error`

### Task 4
Active Command Injection.
Here you get output direct in the browser. 
So lets play around. 
- whoami
- uname -a
- ps -ef
- pwd
- ls -la ../../  

*Tip*
you can still redirect the output in a file.  

`ls -la > ls.txt`

#### What strange text file is in the website root directory?
`drpepper.txt`

#### How many non-root/non-service/non-daemon users are there?
Honnestly I had to google that. 
I found the following: 
 
All users are listed in `/etc/passwd` 
All users with a `/home/` directory are real users. 
I entered 

    cat /etc/passwd > p.txt 	
    cat /etc/passwd | grep /home > p1.txt


The first one shows the hole content of passwd. 
The second one only these which have an /home...
There is one. But the correct answer is 0. found here https://www.thedutchhacker.com/owasp-top-10-on-tryhackme/






#### What version of Ubuntu is running?
For this task we need to know how to find the Ubuntu version. 
search for on the web you will find this command: `lsb_release –a` 
With the knowlege of Task 3 we can enter 
`lsb_release –a > ubuntu.txt` and again browse to the created textfile. 
`18.04.4` 



















