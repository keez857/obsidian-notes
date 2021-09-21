We enumerated the user `admin` with wpscan
We used the old password `P@s5w0rd!` found in [[old passwords]]

We are able to login with `admin:P@s5w0rd!`

---

First thing we try is theme editor 
`appearance > theme editor > twentynineteen > 404.php`


we edit with the reverse php script here:
`https://github.com/ivan-sincek/php-reverse-shell/blob/master/src/php_reverse_shell_older.php`

we gain a shell by going to this link:
`http://10.10.10.29/wordpress/wp-content/themes/twentynineteen/404.php`