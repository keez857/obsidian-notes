### nmap
```bash
nmap -sC -sV 10.10.10.49
Starting Nmap 7.91 ( https://nmap.org ) at 2021-09-25 15:15 EDT
Nmap scan report for 10.10.10.49
Host is up (0.042s latency).
Not shown: 997 filtered ports
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH for_Windows_8.1 (protocol 2.0)
| ssh-hostkey: 
|   3072 9f:a0:f7:8c:c6:e2:a4:bd:71:87:68:82:3e:5d:b7:9f (RSA)
|   256 90:7d:96:a9:6e:9e:4d:40:94:e7:bb:55:eb:b3:0b:97 (ECDSA)
|_  256 f9:10:eb:76:d4:6d:4f:3e:17:f3:93:d6:0b:8c:4b:81 (ED25519)
80/tcp  open  http     Apache httpd 2.4.41 ((Win64) OpenSSL/1.1.1c PHP/7.2.28)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.41 (Win64) OpenSSL/1.1.1c PHP/7.2.28
|_http-title: MegaShopping
443/tcp open  ssl/http Apache httpd 2.4.41 ((Win64) OpenSSL/1.1.1c PHP/7.2.28)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.41 (Win64) OpenSSL/1.1.1c PHP/7.2.28
|_http-title: MegaShopping
| ssl-cert: Subject: commonName=localhost
| Not valid before: 2009-11-10T23:48:47
|_Not valid after:  2019-11-08T23:48:47
|_ssl-date: TLS randomness does not represent time
| tls-alpn:                                                                                                        
|_  http/1.1                                               
```

### gobuster 
```
gobuster dir -u http://10.10.10.49 -w /usr/share/wordlists/dirb/common.txt 
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.10.49
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Timeout:                 10s
===============================================================
2021/09/25 15:19:58 Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 1044]
/.htaccess            (Status: 403) [Size: 1044]
/.htpasswd            (Status: 403) [Size: 1044]
/aux                  (Status: 403) [Size: 1044]
/cgi-bin/             (Status: 403) [Size: 1058]
/com1                 (Status: 403) [Size: 1044]
/com2                 (Status: 403) [Size: 1044]
/com3                 (Status: 403) [Size: 1044]
/con                  (Status: 403) [Size: 1044]
/examples             (Status: 503) [Size: 1058]
/images               (Status: 301) [Size: 336] [--> http://10.10.10.49/images/]
/Images               (Status: 301) [Size: 336] [--> http://10.10.10.49/Images/]
/index.php            (Status: 200) [Size: 12100]                               
/licenses             (Status: 403) [Size: 1203]                                
/lpt2                 (Status: 403) [Size: 1044]                                
/lpt1                 (Status: 403) [Size: 1044]                                
/nul                  (Status: 403) [Size: 1044]                                
/phpmyadmin           (Status: 403) [Size: 1203]                                
/prn                  (Status: 403) [Size: 1044]                                
/server-info          (Status: 403) [Size: 1203]                                
/server-status        (Status: 403) [Size: 1203]                                
/webalizer            (Status: 403) [Size: 1044]                                
```

