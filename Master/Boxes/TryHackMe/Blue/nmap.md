    **nmap -sV -vv -A --script vuln 10.10.40.95**  
  
  
Scanned at 2021-04-05 19:22:17 EDT for 83s  
Not shown: 991 closed ports  
Reason: 991 conn-refused  
PORT STATE SERVICE REASON VERSION  
135/tcp open msrpc syn-ack Microsoft Windows RPC  
139/tcp open netbios-ssn syn-ack Microsoft Windows netbios-ssn  
445/tcp open microsoft-ds syn-ack Windows 7 Professional 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)  
3389/tcp open ssl/ms-wbt-server? syn-ack  
| ssl-cert: Subject: commonName=Jon-PC  
| Issuer: commonName=Jon-PC  
| Public Key type: rsa  
| Public Key bits: 2048  
| Signature Algorithm: sha1WithRSAEncryption  
| Not valid before: 2021-04-04T23:21:43  
| Not valid after: 2021-10-04T23:21:43  
| MD5: 8c39 31ce b1ab 72d0 4bb9 ae69 45a8 b23d  
| SHA-1: c81c f530 a3c4 fdad 02ea 855b b69c 3aa3 e273 6f88  
| -----BEGIN CERTIFICATE-----  
| MIIC0DCCAbigAwIBAgIQKP7L4OphUIFIRNTpw4+FsTANBgkqhkiG9w0BAQUFADAR  
| MQ8wDQYDVQQDEwZKb24tUEMwHhcNMjEwNDA0MjMyMTQzWhcNMjExMDA0MjMyMTQz  
| WjARMQ8wDQYDVQQDEwZKb24tUEMwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK  
| AoIBAQDSijPL8L3IsQvH8Co1/hB7XjI/Bzsj7G/q39b7LHY8mfHMzBmycmOpjRFo  
| 9TeOD2nJ8Kt07ihEyDDAS/oIv2uWUqO2uM3PER3hFe7K8mqCKh+gECm3LYWFZcOh  
| iClJeZ07P+x4PYJ38fUwc+LDuImLzmKCWbG1GUH5/99U7hPp2NUh6LM5jHIAWIQH  
| A6zmFWxA3WQWB9ayaDBgm/++GO81BxDxODsHP4xrn+4Pki19ki8HutPvpaiVbyYn  
| NQQYZH7KtfePb3CHsZ1icWMIjNlD5F4RGF/aZjGwvBzijC+668EdHt4gg4fq6DsW  
| +NEeLFn6kfrTehr8IRUI85sfZqYJAgMBAAGjJDAiMBMGA1UdJQQMMAoGCCsGAQUF  
| BwMBMAsGA1UdDwQEAwIEMDANBgkqhkiG9w0BAQUFAAOCAQEAVeIGRGVJI/6b3KlN  
| IdXn2AnPed0WrXaD1o7+boeF8ULnx6kq3hTFB2xNj7AvsYqcp1GpT7zL4BhUmwvN  
| uEiGdtztqg15M0INJN0iJnyxu0qkhkX2/6aaVofgndWHWgc3et5AC+P1NXGXKmuR  
| pnv6zQbj7rPXk7FEiUyEGUwl3CFV4T/JSwoH7aZ/vB4VaFIQfjFcrfy3VT27KbIS  
| lzRni+HjghCgT2upNSRzMLgn9gTGyQfoDo9MdMVKRiujGbbf7er7yFCFw9cb1E8A  
| jZMhdqZ4c5iNtE3D4jRL44KmCDHm7y45wm5XKJ8K1IeaWbFSSrjewP/tJFNPc85L  
| aSFJyw==  
|\_-----END CERTIFICATE-----  
|\_ssl-date: 2021-04-05T23:23:39+00:00; -1s from scanner time.  
49152/tcp open msrpc syn-ack Microsoft Windows RPC  
49153/tcp open msrpc syn-ack Microsoft Windows RPC  
49154/tcp open msrpc syn-ack Microsoft Windows RPC  
49158/tcp open msrpc syn-ack Microsoft Windows RPC  
49160/tcp open msrpc syn-ack Microsoft Windows RPC  
Service Info: Host: JON-PC; OS: Windows; CPE: cpe:/o:microsoft:windows  
  
Host script results:  
|\_clock-skew: mean: 1h14m59s, deviation: 2h30m00s, median: 0s  
| nbstat: NetBIOS name: JON-PC, NetBIOS user: <unknown>, NetBIOS MAC: 02:a1:26:da:b7:ed (unknown)  
| Names:  
| JON-PC<00> Flags: <unique><active>  
| WORKGROUP<00> Flags: <group><active>  
| JON-PC<20> Flags: <unique><active>  
| WORKGROUP<1e> Flags: <group><active>  
| WORKGROUP<1d> Flags: <unique><active>  
| \\x01\\x02\_\_MSBROWSE\_\_\\x02<01> Flags: <group><active>  
| Statistics:  
| 02 a1 26 da b7 ed 00 00 00 00 00 00 00 00 00 00 00  
| 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
|\_ 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
| p2p-conficker:  
| Checking for Conficker.C or higher...  
| Check 1 (port 25248/tcp): CLEAN (Couldn't connect)  
| Check 2 (port 16043/tcp): CLEAN (Couldn't connect)  
| Check 3 (port 56670/udp): CLEAN (Timeout)  
| Check 4 (port 56336/udp): CLEAN (Failed to receive data)  
|\_ 0/4 checks are positive: Host is CLEAN or ports are blocked  
| smb-os-discovery:  
| OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)  
| OS CPE: cpe:/o:microsoft:windows\_7::sp1:professional  
| Computer name: Jon-PC  
| NetBIOS computer name: JON-PC\\x00  
| Workgroup: WORKGROUP\\x00  
|\_ System time: 2021-04-05T18:23:34-05:00  
| smb-security-mode:  
| account\_used: guest  
| authentication\_level: user  
| challenge\_response: supported  
|\_ message\_signing: disabled (dangerous, but default)  
| smb2-security-mode:  
| 2.02:  
|\_ Message signing enabled but not required  
| smb2-time:  
| date: 2021-04-05T23:23:34  
|\_ start\_date: 2021-04-05T23:21:42  
  
_Host script results:  
|\_samba-vuln-cve-2012-1182: NT\_STATUS\_ACCESS\_DENIED  
|\_smb-vuln-ms10-054: false  
|\_smb-vuln-ms10-061: NT\_STATUS\_ACCESS\_DENIED  
| smb-vuln-ms17-010:  
| VULNERABLE:  
| Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)  
| State: VULNERABLE  
| IDs: CVE:CVE-2017-0143  
| Risk factor: HIGH  
| A critical remote code execution vulnerability exists in Microsoft SMBv1  
| servers (ms17-010).  
|  
| Disclosure date: 2017-03-14  
| References:  
|_ [https://blogs.technet.microsoft.com/msrc/2017/05/12/customer-guidance-for-wannacrypt-attacks/](https://blogs.technet.microsoft.com/msrc/2017/05/12/customer-guidance-for-wannacrypt-attacks/)_|_ [https://technet.microsoft.com/en-us/library/security/ms17-010.aspx](https://technet.microsoft.com/en-us/library/security/ms17-010.aspx)_|\__ [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-0143](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-0143)