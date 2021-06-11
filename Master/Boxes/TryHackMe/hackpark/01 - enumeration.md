```bash

nmap -A 10.10.45.183                                                                                      
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-11 15:54 EDT
Nmap scan report for 10.10.45.183
Host is up (0.12s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE            VERSION
80/tcp   open  http               Microsoft IIS httpd 8.5
| http-methods: 
|_  Potentially risky methods: TRACE
| http-robots.txt: 6 disallowed entries 
| /Account/*.* /search /search.aspx /error404.aspx 
|_/archive /archive.aspx
|_http-server-header: Microsoft-IIS/8.5
|_http-title: hackpark | hackpark amusements
3389/tcp open  ssl/ms-wbt-server?
| ssl-cert: Subject: commonName=hackpark
| Not valid before: 2021-06-10T19:49:42
|_Not valid after:  2021-12-10T19:49:42
|_ssl-date: 2021-06-11T19:55:09+00:00; 0s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```


---

```bash
gobuster dir -u 10.10.45.183 -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-directories.txt -x php,html,js
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.45.183
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-directories.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              js,php,html
[+] Timeout:                 10s
===============================================================
2021/06/11 16:02:21 Starting gobuster in directory enumeration mode
===============================================================
/search               (Status: 200) [Size: 8394]
/scripts              (Status: 301) [Size: 151] [--> http://10.10.45.183/scripts/]
/admin                (Status: 302) [Size: 172] [--> http://10.10.45.183/Account/login.aspx?ReturnURL=/admin]
/aspnet_client        (Status: 301) [Size: 157] [--> http://10.10.45.183/aspnet_client/]                     
/blog                 (Status: 500) [Size: 1208]                                                             
/contact              (Status: 200) [Size: 9922]                                                             
/content              (Status: 301) [Size: 151] [--> http://10.10.45.183/content/]                           
/Scripts              (Status: 301) [Size: 151] [--> http://10.10.45.183/Scripts/]                           
/archives             (Status: 200) [Size: 8313]                                                             
/Admin                (Status: 302) [Size: 172] [--> http://10.10.45.183/Account/login.aspx?ReturnURL=/Admin]
/archive              (Status: 200) [Size: 8312]                                                             
/account              (Status: 301) [Size: 151] [--> http://10.10.45.183/account/]                           
/Search               (Status: 200) [Size: 8394]                                                             
/contacts             (Status: 200) [Size: 9923]                                                             
/fonts                (Status: 301) [Size: 149] [--> http://10.10.45.183/fonts/]                             
/custom               (Status: 301) [Size: 150] [--> http://10.10.45.183/custom/]                            
/setup                (Status: 302) [Size: 174] [--> http://10.10.45.183/Account/login.aspx?ReturnUrl=%2fsetup
```