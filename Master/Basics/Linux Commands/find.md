finding SUID binaries
 ```bash
 
find / -user root -perm /4000 2>/dev/null  
find / -perm -u=s -type f 2>/dev/null
find / -type f -perm -4000 2>/dev/null

```
  
Finding SUID/SGID executables
```bash

find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null`  
  
```
  
  
find command for finding new items to help with priv esc [change date to date box was made]
```

find / -newermt "2021-02-12" -newermt "2021-02-19" -ls| grep -v ' /etc\| /var/lib\| /sys\| /proc\| /boot'

```