## /hidden directory has the following:

C0ldd, you changed Hugo's password, when you can send it to him so he can continue uploading his articles. Philip


## Users found using wpscan:
hugo\
philip\
c0ldd

## using wpscan to brute force, we get c0ldd's credentials
```bash 
wpscan --url http://10.10.228.176/ -U c0ldd,hugo,philip /usr/share/wordlists/rockyou.txt

[!] Valid Combinations Found:
 | Username: c0ldd, Password: 9876543210

```


### several options after logging in. first step would be to try to get a shell using php reverse shell. we can try to upload a php plugin or edit an existing page.

I chose to change the 404.php page to exec the php reverse shell. 
This can be edited by going to Appearance > Editor

Visiting the 
http://10.10.226.162/wp-content/themes/twentyfifteen/404.php
will exec the code.


