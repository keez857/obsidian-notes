# finding SUID binaries
 ```bash
find / -user root -perm /4000 2>/dev/null  
find / -perm -u=s -type f 2>/dev/null
find / -type f -perm -4000 2>/dev/null
```
  
**Finding SUID/SGID executables**  
```bash
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null`  
  
```
  
  
**Check /etc/chron for cronjobs**  
cat /etc/crontab  
/etc/cron.d  
  
  
**Check /var/www/**  
  
**Check netstat -plant or -l** 
  
Look for SSH keys /home/<user>/.ssh