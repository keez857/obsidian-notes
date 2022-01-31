### listing shares
```
smbclient -N -L //10.10.189.145
```

### connecting as user
```
smbclient -L //10.10.104.38 -U DOMAIN/user
```
or just simply:
```
smbclient //<host>
```


--- 

### enum4linux

`enum4linux -a <host>`


---


### metasploit modules

`auxiliary/scanner/smb/smb_version`