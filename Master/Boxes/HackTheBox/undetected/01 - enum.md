## initial nmap

```
nmap -p22,80 -A -sC -sV -T4 10.129.138.149
Starting Nmap 7.91 ( https://nmap.org ) at 2022-02-19 15:03 EST
Nmap scan report for 10.129.138.149
Host is up (0.047s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2 (protocol 2.0)
| ssh-hostkey: 
|   3072 be:66:06:dd:20:77:ef:98:7f:6e:73:4a:98:a5:d8:f0 (RSA)
|   256 1f:a2:09:72:70:68:f4:58:ed:1f:6c:49:7d:e2:13:39 (ECDSA)
|_  256 70:15:39:94:c2:cd:64:cb:b2:3b:d1:3e:f6:09:44:e8 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Diana's Jewelry
```

## nmap udp
```
68/udp open|filtered dhcpc
```


## feroxbuster dir
```
301        9l       28w      313c http://undetected.htb/js
301        9l       28w      317c http://undetected.htb/images
301        9l       28w      314c http://undetected.htb/css
301        9l       28w      316c http://undetected.htb/fonts
301        9l       28w      316c http://undetected.htb/icons
403        9l       28w      279c http://undetected.htb/server-status
301        9l       28w      322c http://undetected.htb/icons/small
```


## feroxbuster 2

```
301        9l       28w      321c http://store.djewelry.htb/js
301        9l       28w      325c http://store.djewelry.htb/images
301        9l       28w      322c http://store.djewelry.htb/css
200      122l      337w     4129c http://store.djewelry.htb/login.php
200      134l      354w     4396c http://store.djewelry.htb/cart.php
200      229l      550w     7447c http://store.djewelry.htb/products.php
200      195l      475w     6215c http://store.djewelry.htb/index.php
301        9l       28w      324c http://store.djewelry.htb/fonts
301        9l       28w      325c http://store.djewelry.htb/vendor
301        9l       28w      329c http://store.djewelry.htb/vendor/bin
403        9l       28w      283c http://store.djewelry.htb/server-status
301        9l       28w      333c http://store.djewelry.htb/vendor/symfony
200        0l        0w        0c http://store.djewelry.htb/vendor/autoload.php
301        9l       28w      334c http://store.djewelry.htb/vendor/composer
301        9l       28w      334c http://store.djewelry.htb/vendor/doctrine
```

