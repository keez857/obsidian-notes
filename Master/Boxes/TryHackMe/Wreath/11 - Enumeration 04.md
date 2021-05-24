We can first use `whoami /priv` to check current user privs

We can also use `whoami /groups`


looking for non-default services:  

`wmic service get name,displayname,pathname,startmode | findstr /v /i "C:\Windows"`

This lists all of the services on the system, then filters so that only services that are _not_ in the `C:\Windows` directory are returned. This should cut out most of the core Windows services (which are unlikely to be vulnerable to this kind of vulnerability), leaving us with primarily lesser-known, user-installed services.


**Notice that one of the paths does not have quotation marks around it.**

SystemExplorerHelpService is exploitable via 
**Unquoted Service Path** attack

---

Check to see which account the service runs under

`sc qc SystemExplorerHelpService`

We can see the service is running on a local system account
`SERVICE_START_NAME : LocalSystem`

Let's check the permissions on the directory. If we can write to it, we are golden:  
`powershell "get-acl -Path 'C:\Program Files (x86)\System Explorer' | format-list"`

We cab see we have full control of the exploitable directory
`Access : BUILTIN\Users Allow  FullControl`


