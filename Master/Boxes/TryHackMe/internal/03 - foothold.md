after grabbing a shell, we poke around and try to find config files

we find the wpconfig in `/var/www/html/wordpress/wp-config.php`

From this config file we can file credentials for MySQL
```bash
/** MySQL database username */
define( 'DB_USER', 'wordpress' );

/** MySQL database password */
define( 'DB_PASSWORD', 'wordpress123' );
```

after snooping around we find /opt/wp-save.txt which contains creds:

```bash
Bill,

Aubreanna needed these credentials for something later.  Let her know you have them and where they are.

aubreanna:bubb13guM!@#123
```

