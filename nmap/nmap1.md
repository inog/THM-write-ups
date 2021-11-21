# Nmap Live Host Discovery room on THM 
[thm] https://tryhackme.com/room/nmap01

This writeup is not completed

## Task 1 Introduction

Just read.
.
.
.


## Task 5 Nmap Host Discovery Using ARP

Remember: arp -> Address Resolution Protocol - [wiki] https://en.wikipedia.org/wiki/Address_Resolution_Protocol
The option `-sn` stands for no port scan. `nmap -sn TARGETS` 
The option `-PR` only arp scan 


## Task 6 Nmap Host Discovery Using ICMP

`-icmp` ->Internet Control Message Protocol  https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol
`-PE` -> ICMP Ping Types


### What is the option required to tell Nmap to use ICMP Timestamp to discover live hosts?
`-PP`

### What is the option required to tell Nmap to use ICMP Address Mask to discover live hosts?
`-PM`

### What is the option required to tell Nmap to use ICMP Echo to discover life hosts?
'-PE`


## Task 7 Nmap Host Discovery Using TCP and UDP

### Which TCP ping scan does not require a privileged account?
`TCP SYN Ping`

### Which TCP ping scan requires a privileged account?

`TCP ACK Ping`

### What option do you need to add to Nmap to run a TCP SYN ping scan on the telnet port?

`-PS23`
## Task 8 Using Reverse-DNS Lookup

### We want Nmap to issue a reverse DNS lookup for all the possibles hosts on a subnet, hoping to get some insights from the names. What option should we add?

`-R`

# Nmap Live Host Discovery room on THM 
[thm] https://tryhackme.com/room/nmap01


## Task 1 Introduction

Just read.
.
.
.


## Task 5 Nmap Host Discovery Using ARP

Remember: arp -> Address Resolution Protocol - [wiki] https://en.wikipedia.org/wiki/Address_Resolution_Protocol
The option `-sn` stands for no port scan. `nmap -sn TARGETS` 
The option `-PR` only arp scan 


## Task 6 Nmap Host Discovery Using ICMP

`-icmp` ->Internet Control Message Protocol  https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol
`-PE` -> ICMP Ping Types


### What is the option required to tell Nmap to use ICMP Timestamp to discover live hosts?
`-PP`

### What is the option required to tell Nmap to use ICMP Address Mask to discover live hosts?
`-PM`

### What is the option required to tell Nmap to use ICMP Echo to discover life hosts?
'-PE`


## Task 7 Nmap Host Discovery Using TCP and UDP

### Which TCP ping scan does not require a privileged account?
`TCP SYN Ping`

### Which TCP ping scan requires a privileged account?

`TCP ACK Ping`

### What option do you need to add to Nmap to run a TCP SYN ping scan on the telnet port?

`-PS23`



