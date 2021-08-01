### nmap
```bash
nmap -A 10.10.183.49
Starting Nmap 7.91 ( https://nmap.org ) at 2021-07-31 23:11 EDT
Nmap scan report for 10.10.183.49
Host is up (0.12s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         vsftpd 2.0.8 or later
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxrwxrwx    2 111      113          4096 Jun 04  2020 scripts [NSE: writeable]
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.9.0.100
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp  open  ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8b:ca:21:62:1c:2b:23:fa:6b:c6:1f:a8:13:fe:1c:68 (RSA)
|   256 95:89:a4:12:e2:e6:ab:90:5d:45:19:ff:41:5f:74:ce (ECDSA)
|_  256 e1:2a:96:a4:ea:8f:68:8f:cc:74:b8:f0:28:72:70:cd (ED25519)
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)
Service Info: Host: ANONYMOUS; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_nbstat: NetBIOS name: ANONYMOUS, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb-os-discovery:                                                                              
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)                                                         
|   Computer name: anonymous                                                                     
|   NetBIOS computer name: ANONYMOUS\x00                                                         
|   Domain name: \x00                                                                            
|   FQDN: anonymous                                                                              
|_  System time: 2021-08-01T03:11:31+00:00                                                       
| smb-security-mode:                                                                             
|   account_used: guest                                                                          
|   authentication_level: user                                                                   
|   challenge_response: supported                                                                
|_  message_signing: disabled (dangerous, but default)                                           
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-08-01T03:11:31
|_  start_date: N/A

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 34.75 seconds
```


### enum4linux

```
 ========================== 
|    Target Information    |
 ========================== 
Target ........... 10.10.183.49
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ===================================== 
|    Session Check on 10.10.183.49    |
 ===================================== 
[+] Server 10.10.183.49 allows sessions using username '', password ''



 ========================================= 
|    Share Enumeration on 10.10.183.49    |
 ========================================= 

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        pics            Disk      My SMB Share Directory for Pics
        IPC$            IPC       IPC Service (anonymous server (Samba, Ubuntu))
		
		
 ========================================= 
|    Share Enumeration on 10.10.183.49    |
 ========================================= 

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        pics            Disk      My SMB Share Directory for Pics
        IPC$            IPC       IPC Service (anonymous server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available

[+] Attempting to map shares on 10.10.183.49
//10.10.183.49/print$   Mapping: DENIED, Listing: N/A
//10.10.183.49/pics     Mapping: OK, Listing: OK
//10.10.183.49/IPC$     [E] Can't understand response:
NT_STATUS_OBJECT_NAME_NOT_FOUND listing \*
		


```