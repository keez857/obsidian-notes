```bash
nmap -A -sC 10.10.10.223
Starting Nmap 7.91 ( https://nmap.org ) at 2021-05-08 23:55 EDT
Nmap scan report for 10.10.10.223
Host is up (0.045s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 cc:ca:43:d4:4c:e7:4e:bf:26:f4:27:ea:b8:75:a8:f8 (RSA)
|   256 85:f3:ac:ba:1a:6a:03:59:e2:7e:86:47:e7:3e:3c:00 (ECDSA)
|_  256 e7:e9:9a:dd:c3:4a:2f:7a:e1:e0:5d:a2:b0:ca:44:a8 (ED25519)                                               
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))                                                             
|_http-server-header: Apache/2.4.29 (Ubuntu)                                                                    
|_http-title: Apache2 Ubuntu Default Page: It works                                                             
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel                                                         
                                                                                                                
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .                  
Nmap done: 1 IP address (1 host up) scanned in 9.10 seconds
```
