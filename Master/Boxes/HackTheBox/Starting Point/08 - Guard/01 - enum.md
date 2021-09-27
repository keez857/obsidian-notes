### nmap
```bash
nmap -A 10.10.10.50
Starting Nmap 7.91 ( https://nmap.org ) at 2021-09-25 22:23 EDT
Nmap scan report for 10.10.10.50
Host is up (0.054s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 2a:64:23:e0:a7:ec:1d:3b:f0:63:72:a7:d7:05:57:71 (RSA)
|   256 b3:86:5d:3d:c9:d1:70:ea:d6:3d:36:a6:c5:f2:be:5d (ECDSA)
|_  256 c0:5b:13:0f:d6:e6:d1:71:2d:55:e2:4a:e2:27:0e:c2 (ED25519)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```

We can use the ssh key from Markup to login as Daniel
