# Topics to learn

* [Subnets](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/)
* [Network Layer](https://www.cloudflare.com/learning/network-layer/what-is-the-network-layer/)


# Sysadmin Commands/Concepts

* passwd file (/etc/passwd) - This file shows all the users in the system, their grp etc
* shadow file (/etc/shadow) - Stores the password hash

# Tools

* [Pimp my Kali](https://github.com/Dewalt-arch/pimpmykali)
* [Dehashed - Password Leaks DB](https://www.dehashed.com/)
* [Subdomains Hunter - To view all domains for weakness](https://crt.sh/)
* [Website Tech Stack Viewer - Wappalyzer](https://chrome.google.com/webstore/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg/related?hl=en-US)
* 

# kali Commands 

**NETSTAT** - netstat provides statistics about all active connections so you can find out which computers or networks a PC is connected to.

usage: `netstat -ano`

e.g.
```
projects » netstat -ano | grep "tcp"                                                      
tcp4       0      0  192.168.2.11.57961     170.114.52.10.443      ESTABLISHED
tcp4       0      0  192.168.2.11.57960     170.114.52.10.443      ESTABLISHED
tcp4       0      0  127.0.0.1.63712        127.0.0.1.57949        ESTABLISHED
tcp4       0      0  127.0.0.1.57949        127.0.0.1.63712        ESTABLISHED
tcp4       0      0  127.0.0.1.49319        127.0.0.1.57948        ESTABLISHED
tcp4       0      0  127.0.0.1.57948        127.0.0.1.49319        ESTABLISHED

```
---

**ARP SCAN** - scans the network that the device is connected for devices, the output lists device ip addresses, MAC addresses and Device Description.

usage: `arp-scan -l`

e.g.
```
# arp-scan -l
Interface: wlan1, type: EN10MB, MAC: 00:c0:ca:96:65:fe, IPv4: 192.168.1.137
Starting arp-scan 1.9.8 with 256 hosts (https://github.com/royhills/arp-scan)
192.168.1.1     f8:27:2e:0b:ff:06       Mercku
192.168.1.160   f4:fe:fb:c3:55:0f       Samsung Electronics Co.,Ltd
192.168.1.118   a8:bb:50:bc:c2:b9       WiZ IoT Company Limited
192.168.1.166   e4:23:54:1c:44:77       SHENZHEN FUZHI SOFTWARE TECHNOLOGY CO.,LTD
192.168.1.155   ac:89:95:8f:51:e9       AzureWave Technology Inc.
192.168.1.171   88:66:5a:13:fb:67       Apple, Inc.
```

---

**NETDISCOVER** - Newer version of arp scan, here we can also specify subnet ranges for the scan.

usage: `netdiscover -r 192.168.1.0/24`

e.g.
```
 Currently scanning: finished   |   Screen View: Unique Hosts

 43 Captured ARP Req/Rep packets, from 5 hosts.   Total size: 1806
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname
 -----------------------------------------------------------------------------
 192.168.1.1     f8:27:2e:0b:ff:06     39    1638  Mercku
 192.168.1.145   cc:f4:11:b3:de:d1      1      42  Google, Inc.
 192.168.1.160   f4:fe:fb:c3:55:0f      1      42  Samsung Electronics Co.,Ltd
 192.168.1.166   e4:23:54:1c:44:77      1      42  SHENZHEN FUZHI SOFTWARE TECHNOLOGY CO.,LTD
 192.168.1.155   ac:89:95:8f:51:e9      1      42  AzureWave Technology Inc.
```
---

**NMAP** - Network mapper tool, for a given machine ip, we can use nmap to scan all the open ports and services in that machine.

usage: `nmap -T4 -p- -A <ip_address>`
* T is the speed of the scan, the scan speeds are from 1 (slowest + through) to 5 (fast + not through) 
* p is the port number, `-` means everyting
* A means show all info

e.g.
```
# nmap -T4 -p 80 -A 192.168.1.160
Starting Nmap 7.93 ( https://nmap.org ) at 2023-01-08 05:30 UTC
Nmap scan report for Samsung.lan (192.168.1.160)
Host is up (0.0071s latency).

PORT   STATE  SERVICE VERSION
80/tcp closed http
MAC Address: F4:FE:FB:C3:55:0F (Samsung Electronics)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   7.12 ms Samsung.lan (192.168.1.160)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 3.81 seconds
```
---

**** - 

usage: ` `

e.g.
```
```
---