### nmap

```bash
nmap -A 10.10.10.46
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-24 22:55 EDT
Nmap scan report for 10.10.10.46
Host is up (0.053s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 8.0p1 Ubuntu 6build1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 c0:ee:58:07:75:34:b0:0b:91:65:b2:59:56:95:27:a4 (RSA)
|   256 ac:6e:81:18:89:22:d7:a7:41:7d:81:4f:1b:b8:b2:51 (ECDSA)
|_  256 42:5b:c3:21:df:ef:a2:0b:c9:5e:03:42:1d:69:d0:28 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: MegaCorp Login
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 9.62 seconds
```

---

ftp credential we are supposed to just magically know:
```
ftpuser:mc@F1l3ZilL4
```

after logging into ftp we get backup.zip

backup.zip is password protected. we can use zip2john to crack the pw
`zip2john backup.zip > crack.txt`
`john crack.txt`

We get the password for the zip file: `741852963`

---

It unzips two files: `index.php` and a `style.css` file

inside index.php we find credentials:
```
f($_POST['username'] === 'admin' && md5($_POST['password']) === "2cb42f8734ea607eefed3b70af13bbd3"
```


we put the password hash in crackstation we end up with these creds:
`admin:qwerty789`

We use these to log into the web app

---










