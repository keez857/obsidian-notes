sudo -l does not reveal anything. next thing i checked was `groups`
we see that there is an `lxd` group which means we can use the exploit found here: 

`https://book.hacktricks.xyz/linux-unix/privilege-escalation/interesting-groups-linux-pe/lxd-privilege-escalation`

I use method 2

once you get a tar.gz file you need to get this file onto the victim machine

---

lxd init portion:

```
Would you like to use LXD clustering? (yes/no) [default=no]: 
Do you want to configure a new storage pool? (yes/no) [default=yes]: no
Would you like to connect to a MAAS server? (yes/no) [default=no]: 
Would you like to create a new local network bridge? (yes/no) [default=yes]: no
Would you like to configure LXD to use an existing bridge or host interface? (yes/no) [default=no]: no
Would you like LXD to be available over the network? (yes/no) [default=no]: no
Would you like stale cached images to be updated automatically? (yes/no) [default=yes] no
Would you like a YAML "lxd init" preseed to be printed? (yes/no) [default=no]: no
```

---

Once you have the root shell, remember you mounted a file share into `/mnt/`
