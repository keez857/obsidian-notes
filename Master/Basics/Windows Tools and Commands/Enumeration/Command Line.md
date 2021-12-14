`systeminfo` for general info

---

We can first use `whoami /priv` to check current user privs

We can also use `whoami /groups`

---

`net user` will display all local users on box
`net user /domain` will display all domain users

`net localgroup` will show local PC usergroups


`tasklist` lists all running processes
`tasklist /svc` lists all services hosted in each process

`icacls file` will check permissions of a file

`schtasks` will check for scheduled tasks
`schtasks /query /v /fo LIST` more detail


---

### services

`wmic service list`

looking for non-default services:  

`
wmic service get name,displayname,pathname,startmode | findstr /v /i "C:\Windows"
`

---

Searching for files

`where /r <location> <file>`
ex: `where /r c:\ flag*`

---

Start powershell (-ep will bypass exec policy allowing you to run scripts easily)
`powershell -ep bypass`