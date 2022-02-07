## finding SUID binaries
 ```bash
find / -user root -perm /4000 2>/dev/null  
find / -perm -u=s -type f 2>/dev/null
find / -type f -perm -4000 2>/dev/null
```

---

## finding SUID/SGID executables
```bash

find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2>/dev/null  
  
```
 ---

### Check user groups
`groups`

---

### cronjobs

`cat /etc/crontab` 
`cat /etc/cron.d`  
`crontab -l`
  ---
  
## directories to search
```
/var/www/
/opt/
```
  
---

### check open ports
`netstat -plant or tunlp`

---


### looking for ssh keys
  
`Look for SSH keys /home/<user>/.ssh`
	
	
### searching for for txt files
`find / -iname "*.txt"`


### os enumeration
`hostnamectl`