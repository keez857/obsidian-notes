Now that we have a shell, we should go check that `config.php` file we weren't able to read earlier.

It's located in `/var/www/html/login/config.php`

This gives us creds `admin:thisisagoodpassword`

We try using this password to `su john` and it works

We can also just ssh in as john

Remember to grab the user.txt

---

running `sudo -l` we see john can run `/usr/bin/find` as root

This is an easy gtfobin lookup. We run this command to get root

`sudo find . -exec /bin/sh \; -quit`

