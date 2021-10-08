### nmap
```bash
PORT     STATE SERVICE       VERSION                                                                                 
53/tcp   open  domain        Simple DNS Plus                                                                         
80/tcp   open  http          Microsoft IIS httpd 10.0                                                                
| http-methods:                                                                                                      
|   Supported Methods: OPTIONS TRACE GET HEAD POST                                                                   
|_  Potentially risky methods: TRACE                                                                                 
|_http-server-header: Microsoft-IIS/10.0                                                                             
|_http-title: HTB Printer Admin Panel                                                                                
88/tcp   open  kerberos-sec  Microsoft Windows Kerberos (server time: 2021-10-06 03:19:51Z)
135/tcp  open  msrpc         Microsoft Windows RPC
389/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: return.local0., Site: Default-First-Site-Name)
445/tcp  open  microsoft-ds?
464/tcp  open  kpasswd5?
593/tcp  open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp  open  tcpwrapped
3268/tcp open  ldap          Microsoft Windows Active Directory LDAP (Domain: return.local0., Site: Default-First-Site-Name)
3269/tcp open  tcpwrapped
```


### enum4linux
```             
Target ........... 10.129.230.186                                                                                    
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


Domain Name: RETURN                                                                                                  
Domain Sid: S-1-5-21-3750359090-2939318659-876128439
```

