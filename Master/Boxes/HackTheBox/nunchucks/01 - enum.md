## nmap
`nmap -A -p22,80,443 -sC -sV 10.10.11.122`

```
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 6c:14:6d:bb:74:59:c3:78:2e:48:f5:11:d8:5b:47:21 (RSA)
|   256 a2:f4:2c:42:74:65:a3:7c:26:dd:49:72:23:82:72:71 (ECDSA)
|_  256 e1:8d:44:e7:21:6d:7c:13:2f:ea:3b:83:58:aa:02:b3 (ED25519)
80/tcp  open  http     nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to https://nunchucks.htb/
443/tcp open  ssl/http nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Nunchucks - Landing Page
| ssl-cert: Subject: commonName=nunchucks.htb/organizationName=Nunchucks-Certificates/stateOrProvinceName=Dorset/countryName=UK
| Subject Alternative Name: DNS:localhost, DNS:nunchucks.htb
| Not valid before: 2021-08-30T15:42:24
|_Not valid after:  2031-08-28T15:42:24
| tls-alpn: 
|_  http/1.1
| tls-nextprotoneg: 
|_  http/1.1
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 18.33 seconds

```

---

## nikto
```
nikto -h http://nunchucks.htb
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          10.10.11.122
+ Target Hostname:    nunchucks.htb
+ Target Port:        80
+ Start Time:         2022-02-09 23:15:06 (GMT-5)
---------------------------------------------------------------------------
+ Server: nginx/1.18.0 (Ubuntu)
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ Root page / redirects to: https://nunchucks.htb/
+ No CGI Directories found (use '-C all' to force check all possible dirs)
+ 7785 requests: 0 error(s) and 3 item(s) reported on remote host
+ End Time:           2022-02-09 23:21:39 (GMT-5) (393 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

```

---

## gobuster

http redirects to https so we need to add the `-k` flag for no TLS validation and scan `https://nunchucks.htb`

we also need to exclude the `200` status code with `-b 200`


---

## gobuster vhost

`gobuster vhost -u https://nunchucks.htb -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt -k -r -t 25`

```
Found: store.nunchucks.htb (Status: 200) [Size: 4029]
```



