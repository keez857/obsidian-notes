### possible vulns

80/tcp - Apache httpd 1.3.20

mod_ssl/2.8.4 - mod_ssl  <2.8.7 are vulnerable to remote buffer overflow which may allow remote shell (CVE-2002.0082)


SMB - Samba 2.2.1a

Webalizer v2.01


---

### SMB - samba enum

`searchsploit samba 2.2`

There are numerous Remote Buffer Overflow exploits for samba 2.2

More specifically we want to look at `call_trans2open`

---

### modssl enum

Googling reveals mod_ssl < 2.8.7 is vulnerable to remote buffer overflow (CVE-2002-0082)

https://www.exploit-db.com/exploits/764
https://github.com/heltonWernik/OpenLuck


