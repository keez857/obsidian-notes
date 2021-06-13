### nmap
```bash
nmap -A 10.10.206.115
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-13 19:43 EDT
Nmap scan report for 10.10.206.115
Host is up (0.12s latency).
Not shown: 996 closed ports
PORT      STATE    SERVICE VERSION
22/tcp    open     ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 68:ed:7b:19:7f:ed:14:e6:18:98:6d:c5:88:30:aa:e9 (RSA)
|   256 5c:d6:82:da:b2:19:e3:37:99:fb:96:82:08:70:ee:9d (ECDSA)
|_  256 d2:a9:75:cf:2f:1e:f5:44:4f:0b:13:c2:0f:d7:37:cc (ED25519)
80/tcp    open     http    Apache httpd 2.4.6 ((CentOS) PHP/5.6.40)
|_http-generator: Joomla! - Open Source Content Management
| http-robots.txt: 15 disallowed entries 
| /joomla/administrator/ /administrator/ /bin/ /cache/ 
| /cli/ /components/ /includes/ /installation/ /language/ 
|_/layouts/ /libraries/ /logs/ /modules/ /plugins/ /tmp/
|_http-server-header: Apache/2.4.6 (CentOS) PHP/5.6.40
|_http-title: Home
3306/tcp  open     mysql   MariaDB (unauthorized)
16016/tcp filtered unknown

```

---

### gobuster

```go
gobuster dir -u 10.10.206.115 -w /usr/share/wordlists/dirb/common.txt -x php,html -t 50    
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.206.115
[+] Method:                  GET
[+] Threads:                 50
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              php,html
[+] Timeout:                 10s
===============================================================
2021/06/13 19:45:24 Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 211]
/.hta                 (Status: 403) [Size: 206]
/.htpasswd            (Status: 403) [Size: 211]
/.hta.html            (Status: 403) [Size: 211]
/.htpasswd.php        (Status: 403) [Size: 215]
/.htaccess.php        (Status: 403) [Size: 215]
/.htpasswd.html       (Status: 403) [Size: 216]
/.hta.php             (Status: 403) [Size: 210]
/.htaccess.html       (Status: 403) [Size: 216]
/administrator        (Status: 301) [Size: 243] [--> http://10.10.206.115/administrator/]
/bin                  (Status: 301) [Size: 233] [--> http://10.10.206.115/bin/]          
/cache                (Status: 301) [Size: 235] [--> http://10.10.206.115/cache/]        
/cgi-bin/.html        (Status: 403) [Size: 215]                                          
/cgi-bin/             (Status: 403) [Size: 210]                                          
/components           (Status: 301) [Size: 240] [--> http://10.10.206.115/components/]   
/configuration.php    (Status: 200) [Size: 0]                                            
/images               (Status: 301) [Size: 236] [--> http://10.10.206.115/images/]       
/includes             (Status: 301) [Size: 238] [--> http://10.10.206.115/includes/]     
/index.php            (Status: 200) [Size: 9280]                                         
/index.php            (Status: 200) [Size: 9280]                                         
/layouts              (Status: 301) [Size: 237] [--> http://10.10.206.115/layouts/]      
/language             (Status: 301) [Size: 238] [--> http://10.10.206.115/language/]     
/libraries            (Status: 301) [Size: 239] [--> http://10.10.206.115/libraries/]    
/media                (Status: 301) [Size: 235] [--> http://10.10.206.115/media/]        
/modules              (Status: 301) [Size: 237] [--> http://10.10.206.115/modules/]      
/plugins              (Status: 301) [Size: 237] [--> http://10.10.206.115/plugins/]      
/robots.txt           (Status: 200) [Size: 836]                                          
/templates            (Status: 301) [Size: 239] [--> http://10.10.206.115/templates/]    
/tmp                  (Status: 301) [Size: 233] [--> http://10.10.206.115/tmp/]          
                                                                                         
===============================================================
2021/06/13 19:46:03 Finished
===============================================================
```
