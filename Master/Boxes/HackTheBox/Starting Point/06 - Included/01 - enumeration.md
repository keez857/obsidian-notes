### nmap

```
nmap -A 10.10.10.55                                                                            
Starting Nmap 7.91 ( https://nmap.org ) at 2021-09-23 01:36 EDT
Nmap scan report for 10.10.10.55
Host is up (0.054s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
| http-title: Site doesn't have a title (text/html; charset=UTF-8).
|_Requested resource was http://10.10.10.55/?file=index.php

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.60 seconds
```


### gobuster


