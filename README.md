# Topics to learn

* [Subnets](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/)
* [Network Layer](https://www.cloudflare.com/learning/network-layer/what-is-the-network-layer/)


# Sysadmin Commands/Concepts

* passwd file (/etc/passwd) - This file shows all the users in the system, their grp etc
* shadow file (/etc/shadow) - Stores the password hash

# Tools

* [Pimp my Kali](https://github.com/Dewalt-arch/pimpmykali)
* [Dehashed - Password Leaks DB](https://www.dehashed.com/)
* [Subdomains Hunter - To view all sub domains for weakness, including cert issuers etc](https://crt.sh/)
* [Website Tech Stack Viewer - Wappalyzer](https://chrome.google.com/webstore/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg/related?hl=en-US)
* [Website Tech Stack Viewer 2 (More Details) - Builtwith.com](https://builtwith.com/)
* [Google Search Syntax](https://ahrefs.com/blog/google-advanced-search-operators/)
  - Search for any files, pwds, leaks in the website etc
  - Google search query language
  - Find the recent cache of the website
  - Search for contents in a particular site
  - Search all urls that contain a particular keyword
  - Show search results before & after a particular date
* [Vulnerable Machine Images](https://www.vulnhub.com/)

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

**SS** - Socket statistics (newer version of netstat) 

usage: `ss -t -a -u -m -e -p -T -O --all`

- shows threads using the socket
- udp ports
- tcp ports
- mempry stats of the port
- process using the port 
- etc

e.g.
```
└─# ss -t -a -u -m -e -p -T -O --all | head -n 2
Netid State  Recv-Q Send-Q Local Address:Port           Peer Address:Port  Process                                                                                                     
udp   UNCONN 0      0            0.0.0.0:51014               0.0.0.0:*      users:(("teamviewerd",pid=858,tid=989,fd=18),("teamviewerd",pid=858,tid=880,fd=18),("teamviewerd",pid=858,tid=879,fd=18),("teamviewerd",pid=858,tid=878,fd=18),("teamviewerd",pid=858,tid=877,fd=18),("teamviewerd",pid=858,tid=876,fd=18),("teamviewerd",pid=858,tid=875,fd=18),("teamviewerd",pid=858,tid=874,fd=18),("teamviewerd",pid=858,tid=868,fd=18),("teamviewerd",pid=858,tid=867,fd=18),("teamviewerd",pid=858,tid=866,fd=18),("teamviewerd",pid=858,tid=865,fd=18),("teamviewerd",pid=858,tid=864,fd=18),("teamviewerd",pid=858,tid=863,fd=18),("teamviewerd",pid=858,tid=862,fd=18),("teamviewerd",pid=858,tid=861,fd=18),("teamviewerd",pid=858,tid=860,fd=18),("teamviewerd",pid=858,tid=859,fd=18),("teamviewerd",pid=858,tid=858,fd=18)) 
```

---

**ARP SCAN** - scans the network that the device is connected for devices, the output lists device ip addresses, MAC addresses and Device Description.

Arp-scan sends ARP packets to hosts on the local network and displays any responses that are received. The network interface to use can be specified with the --interface option. If this option is not present, arp-scan will
search the system interface list for the lowest numbered, configured up interface (excluding loopback).  By default, the ARP packets are sent to the Ethernet broadcast address, ff:ff:ff:ff:ff:ff, but that  can  be  changed
with the --destaddr option.

The  target  hosts  to  scan  may be specified in one of three ways: by specifying the targets on the command line; by specifying a file containing the targets with the --file option; or by specifying the --localnet option
which causes all possible hosts on the network attached to the interface (as defined by the interface address and mask) to be scanned. For hosts specified on the command line, or with the --file option, you can use  either
IP addresses or hostnames.  You can also use network specifications IPnetwork/bits, IPstart-IPend, or IPnetwork:NetMask.

The  list  of target hosts is stored in memory.  Each host in this list uses 28 bytes of memory, so scanning a Class-B network (65,536 hosts) requires about 1.75MB of memory for the list, and scanning a Class-A (16,777,216
hosts) requires about 448MB.

arp-scan supports Ethernet and 802.11 wireless networks. It could also support token ring and FDDI, but they have not been tested. It does not support serial links such as PPP or SLIP, because ARP is not supported on them.

The ARP protocol is a layer-2 (datalink layer) protocol that is used to determine a host's layer-2 address given its layer-3 (network layer) address. ARP was designed to work with any layer-2 and  layer-3  address  format,
but the most common use is to map IP addresses to Ethernet hardware addresses, and this is what arp-scan supports. ARP only operates on the local network, and cannot be routed. Although the ARP protocol makes use of IP ad‐
dresses, it is not an IP-based protocol and arp-scan can be used on an interface that is not configured for IP.

ARP is only used by IPv4 hosts. IPv6 uses NDP (neighbour discovery protocol) instead, which is a different protocol and is not supported by arp-scan.

One ARP packet is sent for each for each target host, with the target protocol address (the ar$tpa field) set to the IP address of this host. If a host does not respond, then the ARP packet will be re-sent once more.   The
maximum number of retries can be changed with the --retry option.  Reducing the number of retries will reduce the scanning time at the possible risk of missing some results due to packet loss.

You  can  specify the bandwidth that arp-scan will use for the outgoing ARP packets with the --bandwidth option.  By default, it uses a bandwidth of 256000 bits per second. Increasing the bandwidth will reduce the scanning
time, but setting the bandwidth too high may result in an ARP storm which can disrupt network operation.  Also, setting the bandwidth too high can send packets faster than the network interface  can  transmit  them,  which
will  eventually  fill the kernel's transmit buffer resulting in the error message: No buffer space available.  Another way to specify the outgoing ARP packet rate is with the --interval option, which is an alternative way
to modify the same underlying parameter.

The time taken to perform a single-pass scan (i.e. with --retry=1) is given by:

time = n*i + t + o

Where n is the number of hosts in the list, i is the time interval between packets (specified with --interval, or calculated from --bandwidth), t is the timeout value (specified with --timeout) and o is the  overhead  time
taken to load the targets into the list and read the MAC/Vendor mapping files.  For small lists of hosts, the timeout value will dominate, but for large lists the packet interval is the most important value.

With  65,536  hosts,  the  default  bandwidth of 256,000 bits/second (which results in a packet interval of 2ms), the default timeout of 500ms, and a single pass ( --retry=1), and assuming an overhead of 1 second, the scan
would take 65536*0.002 + 0.5 + 1 = 132.57 seconds, or about 2 minutes 13 seconds.

Any part of the outgoing ARP packet may be modified through the use of the various --arpXXX options.  The use of some of these options may make the outgoing ARP packet non RFC compliant. Different operating systems  handle
the various non standard ARP packets in different ways, and this may be used to fingerprint these systems.  See arp-fingerprint(1) for information about a script which uses these options to fingerprint the target operating
system.

The table below summarises the options that change the outgoing ARP packet. In this table, the Field column gives the ARP packet field name from RFC 826, Bits specifies the number of bits in the  field,  Option  shows  the
arp-scan option to modify this field, and Notes gives the default value and any other notes.

```
┌───────────────────────────────────────────────────────────────┐
│                 Outgoing ARP Packet Options                   │
├───────┬──────┬──────────┬─────────────────────────────────────┤
│Field  │ Bits │ Option   │ Notes                               │
├───────┼──────┼──────────┼─────────────────────────────────────┤
│ar$hrd │ 16   │ --arphrd │ Default is 1 (ARPHRD_ETHER)         │
│ar$pro │ 16   │ --arppro │ Default is 0x0800                   │
│ar$hln │ 8    │ --arphln │ Default is 6 (ETH_ALEN)             │
│ar$pln │ 8    │ --arppln │ Default is 4 (IPv4)                 │
│ar$op  │ 16   │ --arpop  │ Default is 1 (ARPOP_REQUEST)        │
│ar$sha │ 48   │ --arpsha │ Default is interface h/w address    │
│ar$spa │ 32   │ --arpspa │ Default is interface IP address     │
│ar$tha │ 48   │ --arptha │ Default is zero (00:00:00:00:00:00) │
│ar$tpa │ 32   │ None     │ Set to the target host IP address   │
└───────┴──────┴──────────┴─────────────────────────────────────┘
```
The  most  commonly used outgoing ARP packet option is --arpspa, which sets the source IP address in the ARP packet.  This option allows the outgoing ARP packet to use a different source IP address from the outgoing inter‐
face address.  With this option it is possible to use arp-scan on an interface with no IP address configured, which can be useful if you want to ensure that the testing host does not interact with the network being tested.

Warning: Setting ar$spa to the destination IP address can disrupt some operating systems, as they assume there is an IP address clash if they receive an ARP request for their own address.

It is also possible to change the values in the Ethernet frame header that precedes the ARP packet in the outgoing packets. The table below summarises the options that change values in the Ethernet frame header.

```
┌───────────────────────────────────────────────────────────────────┐
│                 Outgoing Ethernet Frame Options                   │
├───────────────┬──────┬─────────────┬──────────────────────────────┤
│Field          │ Bits │ Option      │ Notes                        │
├───────────────┼──────┼─────────────┼──────────────────────────────┤
│Dest Address   │ 48   │ --destaddr  │ Default is ff:ff:ff:ff:ff:ff │
│Source Address │ 48   │ --srcaddr   │ Default is interface address │
│Protocol Type  │ 16   │ --prototype │ Default is 0x0806            │
└───────────────┴──────┴─────────────┴──────────────────────────────┘
```
The most commonly used outgoing Ethernet frame option is --destaddr, which sets the destination Ethernet address for the ARP packet.  --prototype is not often used, because it will cause the packet to be interpreted  as  a
different Ethernet protocol.

Any ARP responses that are received are displayed in the following format:

<IP Address>   <Hardware Address>   <Vendor Details>

Where  IP  Address is the IP address of the responding target, Hardware Address is its Ethernet hardware address (also known as the MAC address) and Vendor Details are the vendor details, decoded from the hardware address.
The output fields are separated by a single tab character.

The responses are displayed in the order they are received, which is not always the same order as the requests were sent because some hosts may respond faster than others.

The vendor decoding uses the files ieee-oui.txt, ieee-iab.txt and mac-vendor.txt, which are supplied with arp-scan.  The ieee-oui.txt and ieee-iab.txt files are generated from the OUI and IAB data on the  IEEE  website  at
http://standards-oui.ieee.org/oui/oui.txt  and  http://standards.ieee.org/regauth/oui/iab.txt.   The  Perl scripts get-oui and get-iab, which are included in the arp-scan package, can be used to update these files with the
latest data from the IEEE website.  The mac-vendor.txt file contains other MAC to Vendor mappings that are not covered by the IEEE OUI and IAB files, and can be used to add custom mappings.

Almost all hosts that support IP will respond to arp-scan if they receive an ARP packet with the target protocol address (ar$tpa) set to their IP address.  This includes firewalls and other hosts  with  IP  filtering  that
drop all IP traffic from the testing system. For this reason, arp-scan is a useful tool to quickly determine all the active IP hosts on a given Ethernet network segment.


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

Netdiscover is an active/passive ARP reconnaissance tool, initially developed to gain information about wireless networks without DHCP servers in wardriving scenarios. It can also be used on switched networks. Built on top of libnet and libpcap, it can passively detect online hosts or search for them by sending ARP requests.

Furthermore, it can be used to inspect your network's ARP traffic, or find network addresses using auto scan mode, which will scan for common local networks.

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

**NMAP** 

  Nmap (“Network Mapper”) is an open source tool for network exploration and security auditing. It was designed to rapidly scan large networks, although it works fine against single hosts. Nmap uses raw IP packets in novel
  ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running, what type of packet
  filters/firewalls are in use, and dozens of other characteristics. While Nmap is commonly used for security audits, many systems and network administrators find it useful for routine tasks such as network inventory,
  managing service upgrade schedules, and monitoring host or service uptime.

  The output from Nmap is a list of scanned targets, with supplemental information on each depending on the options used. Key among that information is the “interesting ports table”.  That table lists the port number and
  protocol, service name, and state. The state is either open, filtered, closed, or unfiltered.  Open means that an application on the target machine is listening for connections/packets on that port.  Filtered means that a
  firewall, filter, or other network obstacle is blocking the port so that Nmap cannot tell whether it is open or closed.  Closed ports have no application listening on them, though they could open up at any time. Ports are
  classified as unfiltered when they are responsive to Nmap's probes, but Nmap cannot determine whether they are open or closed. Nmap reports the state combinations open|filtered and closed|filtered when it cannot determine
  which of the two states describe a port. The port table may also include software version details when version detection has been requested. When an IP protocol scan is requested (-sO), Nmap provides information on
  supported IP protocols rather than listening ports.

  In addition to the interesting ports table, Nmap can provide further information on targets, including reverse DNS names, operating system guesses, device types, and MAC addresses.

  A typical Nmap scan is shown in Example 1. The only Nmap arguments used in this example are -A, to enable OS and version detection, script scanning, and traceroute; -T4 for faster execution; and then the hostname.

  Example 1. A representative Nmap scan

      # nmap -A -T4 scanme.nmap.org

      Nmap scan report for scanme.nmap.org (74.207.244.221)
      Host is up (0.029s latency).
      rDNS record for 74.207.244.221: li86-221.members.linode.com
      Not shown: 995 closed ports
      PORT     STATE    SERVICE     VERSION
      22/tcp   open     ssh         OpenSSH 5.3p1 Debian 3ubuntu7 (protocol 2.0)
      | ssh-hostkey: 1024 8d:60:f1:7c:ca:b7:3d:0a:d6:67:54:9d:69:d9:b9:dd (DSA)
      |_2048 79:f8:09:ac:d4:e2:32:42:10:49:d3:bd:20:82:85:ec (RSA)
      80/tcp   open     http        Apache httpd 2.2.14 ((Ubuntu))
      |_http-title: Go ahead and ScanMe!
      646/tcp  filtered ldp
      1720/tcp filtered H.323/Q.931
      9929/tcp open     nping-echo  Nping echo
      Device type: general purpose
      Running: Linux 2.6.X
      OS CPE: cpe:/o:linux:linux_kernel:2.6.39
      OS details: Linux 2.6.39
      Network Distance: 11 hops
      Service Info: OS: Linux; CPE: cpe:/o:linux:kernel

      TRACEROUTE (using port 53/tcp)
      HOP RTT      ADDRESS
      [Cut first 10 hops for brevity]
      11  17.65 ms li86-221.members.linode.com (74.207.244.221)

      Nmap done: 1 IP address (1 host up) scanned in 14.40 seconds

  The newest version of Nmap can be obtained from https://nmap.org. The newest version of this man page is available at https://nmap.org/book/man.html.  It is also included as a chapter of Nmap Network Scanning: The Official
  Nmap Project Guide to Network Discovery and Security Scanning (see https://nmap.org/book/).


usage: `nmap -T4 -p- -A <ip_address>`
* T is the speed of the scan, the scan speeds are from 1 (slowest + through) to 5 (fast + not through) 
* p is the port number, `-` means everyting
* A means show all info

Another e.g.
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

**NIKTO** - 

  Examine a web server to find potential problems and security vulnerabilities, including:
  •   Server and software misconfigurations
  •   Default files and programs
  •   Insecure files and programs
  •   Outdated servers and programs

usage: `nikto -host <hostname/ip> `

e.g.
```
└─# nikto -host https://www.google.com                                                                                                                                                                                                     
- Nikto v2.5.0
---------------------------------------------------------------------------
+ Multiple IPs found: 172.217.1.4, 2607:f8b0:400b:804::2004
+ Target IP:          172.217.1.4
+ Target Hostname:    www.google.com
+ Target Port:        443
---------------------------------------------------------------------------
+ SSL Info:        Subject:  /CN=www.google.com
                   Ciphers:  TLS_AES_256_GCM_SHA384
                   Issuer:   /C=US/O=Google Trust Services LLC/CN=GTS CA 1C3
+ Start Time:         2023-07-01 23:52:48 (GMT0)
---------------------------------------------------------------------------
+ Server: gws
+ /: Cookie 1P_JAR created without the httponly flag. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies
+ /: Uncommon header 'origin-trial' found, with multiple values: (Ap+qNlnLzJDKSmEHjzM5ilaa908GuehlLqGb6ezME5lkhelj20qVzfv06zPmQ3LodoeujZuphAolrnhnPA8w4AIAAABfeyJvcmlnaW4iOiJodHRwczovL3d3dy5nb29nbGUuY29tOjQ0MyIsImZlYXR1cmUiOiJQZXJtaXNzaW9uc1BvbGljeVVubG9hZCIsImV4cGlyeSI6MTY4NTY2Mzk5OX0=,AvudrjMZqL7335p1KLV2lHo1kxdMeIN0dUI15d0CPz9dovVLCcXk8OAqjho1DX4s6NbHbA/AGobuGvcZv0drGgQAAAB9eyJvcmlnaW4iOiJodHRwczovL3d3dy5nb29nbGUuY29tOjQ0MyIsImZlYXR1cmUiOiJCYWNrRm9yd2FyZENhY2hlTm90UmVzdG9yZWRSZWFzb25zIiwiZXhwaXJ5IjoxNjkxNTM5MTk5LCJpc1N1YmRvbWFpbiI6dHJ1ZX0=,).
+ /: The site uses TLS and the Strict-Transport-Security HTTP header is not defined. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security
+ /: An alt-svc header was found which is advertising HTTP/3. The endpoint is: ':443'. Nikto cannot test HTTP/3 over QUIC. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/alt-svc
+ /: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type. See: https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ : Server banner changed from 'gws' to 'sffe'.
+ /crossdomain.xml: Uncommon header 'cross-origin-opener-policy-report-only' found, with contents: same-origin; report-to="static-on-bigtable".
+ /s2/search/social/: Uncommon header 'accept-ch' found, with contents: Sec-CH-UA-Arch, Sec-CH-UA-Bitness, Sec-CH-UA-Full-Version, Sec-CH-UA-Full-Version-List, Sec-CH-UA-Model, Sec-CH-UA-WoW64, Sec-CH-UA-Form-Factor, Sec-CH-UA-Platform, Sec-CH-UA-Platform-Version.
+ /robots.txt: Entry '/index.html?' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /maps/api/place/js/: Uncommon header 'server-timing' found, with contents: gfet4t7; dur=23.
+ /?hl=/: Drupal Link header found with value: </?hl=/>;rel="canonical". See: https://www.drupal.org/
+ /robots.txt: Entry '/?hl=/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/xhtml/search?/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/?hl=*&*&gws_rd=ssl/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/?hl=*&/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/compressiontest/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /patents/related/: Uncommon header 'x-frontend-version' found, with contents: patent-search.search_20230530_RC01.
+ /robots.txt: Entry '/pda/search?/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/wml/search?/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/pda?/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/landing/signout.html' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file
+ /robots.txt: Entry '/xhtml?/' is returned a non-forbidden or redirect HTTP code (200). See: https://portswigger.net/kb/issues/00600600_robots-txt-file

```
---

**** - 

usage: ``

e.g.
```
```

---