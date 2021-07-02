### nmap
```bash
nmap -A 10.10.200.205
Starting Nmap 7.91 ( https://nmap.org ) at 2021-07-01 22:53 EDT
Nmap scan report for 10.10.200.205
Host is up (0.12s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 1b:c2:b6:2d:fb:32:cc:11:68:61:ab:31:5b:45:5c:f4 (DSA)
|   2048 8d:88:65:9d:31:ff:b4:62:f9:28:f2:7d:42:07:89:58 (RSA)
|_  256 40:2e:b0:ed:2a:5a:9d:83:6a:6e:59:31:db:09:4c:cb (ECDSA)
80/tcp open  http    Apache httpd 2.2.22 ((Ubuntu))
| http-robots.txt: 1 disallowed entry 
|_/VlNCcElFSWdTQ0JKSUVZZ1dTQm5JR1VnYVNCQ0lGUWdTU0JFSUVrZ1p5QldJR2tnUWlCNklFa2dSaUJuSUdjZ1RTQjVJRUlnVHlCSklFY2dkeUJuSUZjZ1V5QkJJSG9nU1NCRklHOGdaeUJpSUVNZ1FpQnJJRWtnUlNCWklHY2dUeUJUSUVJZ2NDQkpJRVlnYXlCbklGY2dReUJDSUU4Z1NTQkhJSGNnUFElM0QlM0Q=
|_http-server-header: Apache/2.2.22 (Ubuntu)
|_http-title: 360 No Scope!
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

---

### gobuster
```go
gobuster dir -u 10.10.200.205 -w /usr/share/wordlists/dirb/common.txt 
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.200.205
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Timeout:                 10s
===============================================================
2021/07/01 23:52:29 Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 285]
/.htaccess            (Status: 403) [Size: 290]
/.htpasswd            (Status: 403) [Size: 290]
/button               (Status: 200) [Size: 39148]
/cat                  (Status: 200) [Size: 62048]
/cgi-bin/             (Status: 403) [Size: 289]  
/index                (Status: 200) [Size: 94328]
/index.php            (Status: 200) [Size: 94328]
/iphone               (Status: 200) [Size: 19867]
/login                (Status: 301) [Size: 314] [--> http://10.10.200.205/login/]
/robots.txt           (Status: 200) [Size: 430]                                  
/robots               (Status: 200) [Size: 430]                                  
/server-status        (Status: 403) [Size: 294]                                  
/small                (Status: 200) [Size: 689]                                  
/static               (Status: 200) [Size: 253890]                               
/who                  (Status: 200) [Size: 3847428]                              
                                                                                 
===============================================================
2021/07/01 23:53:29 Finished
```
