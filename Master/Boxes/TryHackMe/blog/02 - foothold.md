ending up using metasploit crop rce exploit to gain a shell

logged in a www-data, checked wp-config and found mysql credentials

`wordpressuser`
`LittleYellowLamp90!@`
LittleYellowLamp90!@

not too useful because we already have wp login creds

`$P$BedNwvQ29vr1TPd80CDl6WnHyjr8te.` kwheel
`$P$BjoFHe8zIyjnQe/CBvaltzzC6ckPcO/` bjoel

---

searching for suid binaries will lead us to find `/usr/sbin/checker`

after lots of googling, i am advised to run `ltrace` on the command so we can observe what happens when the command is run

```
ltrace /usr/sbin/checker
getenv("admin")                                  = "1"
setuid(0)                                        = 0
```

We can try to set a value to admin
`export admin=1`

Then try running `checker` 

This will change our uid=0 giving us root