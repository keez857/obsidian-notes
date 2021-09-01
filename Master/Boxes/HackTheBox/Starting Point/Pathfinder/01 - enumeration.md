### nmap
```bash
nmap -A 10.10.10.30
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-31 22:56 EDT
Nmap scan report for 10.10.10.30
Host is up (0.048s latency).
Not shown: 989 closed ports
PORT     STATE SERVICE       VERSION
53/tcp   open  domain        Simple DNS Plus
88/tcp   open  kerberos-sec  Microsoft Windows Kerberos (server time: 2021-09-01 10:09:55Z)
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: MEGACORP.LOCAL0., Site: Default-First-Site-Name)
445/tcp  open  microsoft-ds?
464/tcp  open  kpasswd5?
593/tcp  open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp  open  tcpwrapped
3268/tcp open  ldap          Microsoft Windows Active Directory LDAP (Domain: MEGACORP.LOCAL0., Site: Default-First-Site-Name)
3269/tcp open  tcpwrapped
Service Info: Host: PATHFINDER; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 7h13m26s
| smb2-security-mode: 
|   2.02:                                                                                          
|_    Message signing enabled and required                                                         
| smb2-time:                                                                                       
|   date: 2021-09-01T10:10:01                                                                      
|_  start_date: N/A                                                                                
                                                                                                   
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .     
Nmap done: 1 IP address (1 host up) scanned in 20.55 seconds
```

### test