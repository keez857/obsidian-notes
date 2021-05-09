feroxbuster -u http://10.10.10.223 -d 2 -x php,html,js

```rust
 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher                    ver: 2.2.3
───────────────────────────┬──────────────────────
     Target Url            │ http://10.10.10.223
     Threads               │ 50
     Wordlist              │ /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
     Status Codes          │ [200, 204, 301, 302, 307, 308, 401, 403, 405]
     Timeout (secs)        │ 7
     User-Agent            │ feroxbuster/2.2.3
     Extensions            │ [php, html, js]
     Recursion Depth       │ 2
     New Version Available │ https://github.com/epi052/feroxbuster/releases/latest
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Cancel Menu™
──────────────────────────────────────────────────
200      375l      964w    10918c http://10.10.10.223/index.html
301        9l       28w      316c http://10.10.10.223/wordpress
301        9l       28w      325c http://10.10.10.223/wordpress/wp-admin
301        9l       28w      328c http://10.10.10.223/wordpress/wp-includes
405        1l        6w       42c http://10.10.10.223/wordpress/xmlrpc.php
301        9l       28w      327c http://10.10.10.223/wordpress/wp-content
301        0l        0w        0c http://10.10.10.223/wordpress/index.php
200        5l       15w      135c http://10.10.10.223/wordpress/wp-trackback.php
200       97l      416w     6534c http://10.10.10.223/wordpress/wp-login.php
403        9l       28w      277c http://10.10.10.223/server-status
200       97l      823w     7278c http://10.10.10.223/wordpress/readme.html
200        0l        0w        0c http://10.10.10.223/wordpress/wp-config.php
[####################] - 1m    719976/719976  0s      found:12      errors:0      
[####################] - 1m    119996/119996  1089/s  http://10.10.10.223
[####################] - 1m    119996/119996  1116/s  http://10.10.10.223/wordpress
```