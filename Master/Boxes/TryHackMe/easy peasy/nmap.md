    nmap -p80,6498,65524 -sV -sC -T4 -Pn -oA 10.10.124.156 10.10.124.156  
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.  
Starting Nmap 7.91 ( [https://nmap.org](https://nmap.org) ) at 2021-04-06 00:25 EDT  
Nmap scan report for 10.10.124.156  
Host is up (0.12s latency).  
  
PORT STATE SERVICE VERSION  
80/tcp open http nginx 1.16.1  
| http-robots.txt: 1 disallowed entry  
|\_/  
|\_http-server-header: nginx/1.16.1  
|\_http-title: Welcome to nginx!  
6498/tcp open ssh OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:  
| 2048 30:4a:2b:22:ac:d9:56:09:f2:da:12:20:57:f4:6c:d4 (RSA)  
| 256 bf:86:c9:c7:b7:ef:8c:8b:b9:94:ae:01:88:c0:85:4d (ECDSA)  
|\_ 256 a1:72:ef:6c:81:29:13:ef:5a:6c:24:03:4c:fe:3d:0b (ED25519)  
65524/tcp open http Apache httpd 2.4.43 ((Ubuntu))  
| http-robots.txt: 1 disallowed entry  
|\_/  
|\_http-server-header: Apache/2.4.43 (Ubuntu)  
|\_http-title: Apache2 Debian Default Page: It works  
Service Info: OS: Linux; CPE: cpe:/o:linux:linux\_kernel  
  
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
Nmap done: 1 IP address (1 host up) scanned in 16.22 seconds  
\------------------------------------------------------------