## nmap
```
nmap -sC -sV -A -p22,80,3000 -T4 10.10.11.120
Starting Nmap 7.91 ( https://nmap.org ) at 2022-02-15 23:33 EST
Nmap scan report for secret.htb (10.10.11.120)
Host is up (0.046s latency).

PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 97:af:61:44:10:89:b9:53:f0:80:3f:d7:19:b1:e2:9c (RSA)
|   256 95:ed:65:8d:cd:08:2b:55:dd:17:51:31:1e:3e:18:12 (ECDSA)
|_  256 33:7b:c1:71:d3:33:0f:92:4e:83:5a:1f:52:02:93:5e (ED25519)
80/tcp   open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: DUMB Docs
3000/tcp open  http    Node.js (Express middleware)
|_http-title: DUMB Docs
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

---

## gobuster

```
/download             (Status: 301) [Size: 183] [--> /download/]
/assets               (Status: 301) [Size: 179] [--> /assets/]  
/docs                 (Status: 200) [Size: 20720]               
/api                  (Status: 200) [Size: 93]                  
/API                  (Status: 200) [Size: 93]                  
/Docs                 (Status: 200) [Size: 20720]               
/Api                  (Status: 200) [Size: 93]                  
/DOCS                 (Status: 200) [Size: 20720]  
```