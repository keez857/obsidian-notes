First thing I did was edit /etc/hosts to include:
```
10.10.10.223	tenet.htb
```

---

http://tenet.htb/index.php/2020/12/16/logs/#comment-2
Reveals the following message:
```
did you remove the sator php file and the backup?? the migration program is incomplete! why would you do this?!
```

---

We have also found 2 usernames from wpscan:
**neil**
**protagonist**

---

Perform a wpscan brute force attack with the two usernames
`wpscan --url tenet.htb -U neil,protagonist -=passwords /usr/share/wordlists/rockyou.txt`