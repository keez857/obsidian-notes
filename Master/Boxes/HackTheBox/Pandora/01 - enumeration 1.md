## nmap 
`nmap -A -sC -sV -T4 -p22,80 10.10.11.136`

```
Starting Nmap 7.91 ( https://nmap.org ) at 2022-02-08 22:15 EST
Nmap scan report for 10.10.11.136
Host is up (0.056s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 24:c2:95:a5:c3:0b:3f:f3:17:3c:68:d7:af:2b:53:38 (RSA)
|   256 b1:41:77:99:46:9a:6c:5d:d2:98:2f:c0:32:9a:ce:03 (ECDSA)
|_  256 e7:36:43:3b:a9:47:8a:19:01:58:b2:bc:89:f6:51:08 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Play | Landing
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.20 seconds

```


---

## feroxbuster
```
301        9l       28w      311c http://pandora.htb/assets
301        9l       28w      314c http://pandora.htb/assets/js
301        9l       28w      318c http://pandora.htb/assets/images
200      907l     2081w    33560c http://pandora.htb/index.html
301        9l       28w      315c http://pandora.htb/assets/css
301        9l       28w      317c http://pandora.htb/assets/fonts
403        9l       28w      276c http://pandora.htb/server-status
```


---

## nikto
```
nikto -h http://10.10.11.136
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          10.10.11.136
+ Target Hostname:    10.10.11.136
+ Target Port:        80
+ Start Time:         2022-02-08 22:19:45 (GMT-5)
---------------------------------------------------------------------------
+ Server: Apache/2.4.41 (Ubuntu)
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ Server may leak inodes via ETags, header found with file /, inode: 8318, size: 5d23e548bc656, mtime: gzip
+ Allowed HTTP Methods: GET, POST, OPTIONS, HEAD 
+ /: A Wordpress installation was found.
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The site uses SSL and the Strict-Transport-Security HTTP header is not defined.
+ The site uses SSL and Expect-CT header is not present.

+ 7890 requests: 0 error(s) and 6 item(s) reported on remote host
+ End Time:           2022-02-08 22:29:31 (GMT-5) (586 seconds)

```

---

## udp nmap scan
We find that port 161 is open on UDP
`sudo nmap -sU -A -sC -sV -p161 10.10.11.136`


```
PORT    STATE SERVICE VERSION
161/udp open  snmp    SNMPv1 server; net-snmp SNMPv3 server (public)
| snmp-info: 
|   enterprise: net-snmp
|   engineIDFormat: unknown
|   engineIDData: 48fa95537765c36000000000
|   snmpEngineBoots: 30
|_  snmpEngineTime: 4h00m29s
| snmp-interfaces: 
|   lo
|     IP address: 127.0.0.1  Netmask: 255.0.0.0
|     Type: softwareLoopback  Speed: 10 Mbps
|     Traffic stats: 1.49 Mb sent, 1.49 Mb received
|   VMware VMXNET3 Ethernet Controller
|     IP address: 10.10.11.136  Netmask: 255.255.254.0
|     MAC address: 00:50:56:b9:aa:a3 (VMware)
|     Type: ethernetCsmacd  Speed: 4 Gbps
|_    Traffic stats: 148.04 Mb sent, 61.54 Mb received
| snmp-netstat: 
|   TCP  0.0.0.0:22           0.0.0.0:0
|   TCP  10.10.11.136:51224   1.1.1.1:53
|   TCP  127.0.0.1:3306       0.0.0.0:0
|   TCP  127.0.0.53:53        0.0.0.0:0
|   UDP  0.0.0.0:161          *:*
|_  UDP  127.0.0.53:53        *:*
| snmp-processes:
891: 
|     Name: sh
|     Path: /bin/sh
|     Params: -c sleep 30; /bin/bash -c '/usr/bin/host_check -u daniel -p HotelBabylon23'

```

