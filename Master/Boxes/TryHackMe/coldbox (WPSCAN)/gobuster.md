```bash 
gobuster dir -u 10.10.127.160 -w /usr/share/wordlists/dirb/common.txt -x php,html,js
```

```bash

/.hta (Status: 403)
/.hta.php (Status: 403)
/.hta.html (Status: 403)
/.hta.js (Status: 403)
/.htaccess (Status: 403)
/.htaccess.php (Status: 403)
/.htaccess.html (Status: 403)
/.htaccess.js (Status: 403)
/.htpasswd (Status: 403)
/.htpasswd.html (Status: 403)
/.htpasswd.js (Status: 403)
/.htpasswd.php (Status: 403)
/hidden (Status: 301)
/index.php (Status: 301)
/index.php (Status: 301)
/readme.html (Status: 200)
/server-status (Status: 403)
/wp-admin (Status: 301)
/wp-blog-header.php (Status: 200)
/wp-config.php (Status: 200)
/wp-content (Status: 301)
/wp-cron.php (Status: 200)
/wp-includes (Status: 301)
/wp-links-opml.php (Status: 200)
/wp-load.php (Status: 200)
/wp-login.php (Status: 200)
/wp-mail.php (Status: 403)
/wp-signup.php (Status: 302)
/wp-trackback.php (Status: 200)
/xmlrpc.php (Status: 200)
/xmlrpc.php (Status: 200)



^f0d192
