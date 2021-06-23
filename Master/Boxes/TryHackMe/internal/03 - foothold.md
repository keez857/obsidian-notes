after grabbing a shell, we poke around and try to find config files

we find the wpconfig in `/var/www/html/wordpress/wp-config.php`

From this config file we can file credentials for MySQL
```bash
/** MySQL database username */
define( 'DB_USER', 'wordpress' );

/** MySQL database password */
define( 'DB_PASSWORD', 'wordpress123' );
```