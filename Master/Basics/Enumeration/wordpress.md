### basic enumeration
```
wpscan --url <url> -e vp,vt,u 
```

### brute forcing password with username
```
wpscan --url http://10.10.228.176/ -U <usernames> --passwords
/usr/share/wordlists/rockyou.txt
```

---

### post login

1) editing themes in `appearance > theme editor > <theme>`
	- usually look for 404.php
	- executing reverse shell here:
		`http://10.10.226.162/wp-content/themes/<THEME>/404.php`
2) 