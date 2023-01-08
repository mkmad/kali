# kali Commands 

[Pimp my Kali](https://github.com/Dewalt-arch/pimpmykali)

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



**NMAP** - Network map tool, 

usage: `nmap `

e.g.
```
```


**** - 

usage: ` `

e.g.
```
```