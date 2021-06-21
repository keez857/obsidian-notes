### nmap

```bash
nmap -A 10.10.65.33
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-20 23:25 EDT
Nmap scan report for 10.10.65.33
Host is up (0.12s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS httpd 10.0
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds  Windows Server 2016 Standard Evaluation 14393 microsoft-ds
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: RELEVANT
|   NetBIOS_Domain_Name: RELEVANT
|   NetBIOS_Computer_Name: RELEVANT
|   DNS_Domain_Name: Relevant
|   DNS_Computer_Name: Relevant
|   Product_Version: 10.0.14393
|_  System_Time: 2021-06-21T03:26:10+00:00
| ssl-cert: Subject: commonName=Relevant
| Not valid before: 2021-06-20T03:25:10
|_Not valid after:  2021-12-20T03:25:10
|_ssl-date: 2021-06-21T03:26:50+00:00; 0s from scanner time.
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:                                                                                               
|_clock-skew: mean: 1h24m00s, deviation: 3h07m52s, median: 0s                                                      
| smb-os-discovery:                                                                                                
|   OS: Windows Server 2016 Standard Evaluation 14393 (Windows Server 2016 Standard Evaluation 6.3)                
|   Computer name: Relevant                                                                                        
|   NetBIOS computer name: RELEVANT\x00                                                                            
|   Workgroup: WORKGROUP\x00                                                                                       
|_  System time: 2021-06-20T20:26:14-07:00                                                                         
| smb-security-mode:                                                                                               
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-06-21T03:26:11
|_  start_date: 2021-06-21T03:25:09

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 57.44 seconds

```

---

### enum4linux

```
enum4linux -a 10.10.65.33
Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Sun Jun 20 23:35:26 2021

 ========================== 
|    Target Information    |                                                                                       
 ==========================                                                                                        
Target ........... 10.10.65.33                                                                                     
RID Range ........ 500-550,1000-1050                                                                               
Username ......... ''                                                                                              
Password ......... ''                                                                                              
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none                                    
                                                                                                 
 =================================================== 
|    Enumerating Workgroup/Domain on 10.10.65.33    |
 =================================================== 
[E] Can't find workgroup/domain


 =========================================== 
|    Nbtstat Information for 10.10.65.33    |
 =========================================== 
Looking up status of 10.10.65.33
No reply from 10.10.65.33

 ==================================== 
|    Session Check on 10.10.65.33    |
 ==================================== 
Use of uninitialized value $global_workgroup in concatenation (.) or string at ./enum4linux.pl line 437.
[E] Server doesn't allow session using username '', password ''.  Aborting remainder of tests.
```

---

### smbclient -L

```
smbclient -L 10.10.65.33
Enter WORKGROUP\keez's password: 

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        nt4wrksv        Disk      
```
