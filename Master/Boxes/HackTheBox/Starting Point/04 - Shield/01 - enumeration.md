### nmap 

```bash

nmap -A 10.10.10.29
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-30 23:07 EDT
Nmap scan report for 10.10.10.29
Host is up (0.046s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE VERSION
80/tcp   open  http    Microsoft IIS httpd 10.0
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
3306/tcp open  mysql   MySQL (unauthorized)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 14.22 seconds

```

### feroxbuster
```rust

feroxbuster -u http://10.10.10.29 -d 2

 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher                    ver: 2.2.3
───────────────────────────┬──────────────────────
     Target Url            │ http://10.10.10.29
     Threads               │ 50
     Wordlist              │ /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
     Status Codes          │ [200, 204, 301, 302, 307, 308, 401, 403, 405]
     Timeout (secs)        │ 7
     User-Agent            │ feroxbuster/2.2.3
     Recursion Depth       │ 2
     New Version Available │ https://github.com/epi052/feroxbuster/releases/latest
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Cancel Menu™
──────────────────────────────────────────────────
301        2l       10w      152c http://10.10.10.29/wordpress
301        2l       10w      161c http://10.10.10.29/wordpress/wp-admin
301        2l       10w      164c http://10.10.10.29/wordpress/wp-includes
301        2l       10w      163c http://10.10.10.29/wordpress/wp-content
301        2l       10w      152c http://10.10.10.29/Wordpress
301        2l       10w      161c http://10.10.10.29/Wordpress/wp-admin
301        2l       10w      163c http://10.10.10.29/Wordpress/wp-content
301        2l       10w      164c http://10.10.10.29/Wordpress/wp-includes
301        2l       10w      152c http://10.10.10.29/WordPress
301        2l       10w      164c http://10.10.10.29/WordPress/wp-includes
301        2l       10w      161c http://10.10.10.29/WordPress/wp-admin
301        2l       10w      163c http://10.10.10.29/WordPress/wp-content

```

### wpscan
```ruby
+] URL: http://10.10.10.29/wordpress/ [10.10.10.29]
[+] Started: Mon Aug 30 23:17:15 2021

Interesting Finding(s):

[+] Headers
 | Interesting Entries:
 |  - Server: Microsoft-IIS/10.0
 |  - X-Powered-By: PHP/7.1.29
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://10.10.10.29/wordpress/xmlrpc.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/             
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/          
                                                                                                   
[+] WordPress readme found: http://10.10.10.29/wordpress/readme.html                               
 | Found By: Direct Access (Aggressive Detection)                                                  
 | Confidence: 100%                                                                                
                                                                                                   
[+] The external WP-Cron seems to be enabled: http://10.10.10.29/wordpress/wp-cron.php             
 | Found By: Direct Access (Aggressive Detection)                                                  
 | Confidence: 60%                                                                                 
 | References:                                                                                     
 |  - https://www.iplocation.net/defend-wordpress-from-ddos                                        
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 5.2.1 identified (Insecure, released on 2019-05-21).
 | Found By: Rss Generator (Passive Detection)
 |  - http://10.10.10.29/wordpress/index.php/feed/, <generator>https://wordpress.org/?v=5.2.1</generator>
 |  - http://10.10.10.29/wordpress/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.2.1</generator>

[i] The main theme could not be detected.

[+] Enumerating Vulnerable Plugins (via Passive Methods)
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] No plugins Found.

[+] Enumerating Vulnerable Themes (via Passive and Aggressive Methods)
 Checking Known Locations - Time: 00:00:05 <===================> (357 / 357) 100.00% Time: 00:00:05
[+] Checking Theme Versions (via Passive and Aggressive Methods)

[i] No themes Found.

[+] Enumerating Timthumbs (via Passive and Aggressive Methods)
 Checking Known Locations - Time: 00:00:28 <=================> (2568 / 2568) 100.00% Time: 00:00:28

[i] No Timthumbs Found.

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:03 <====================> (137 / 137) 100.00% Time: 00:00:03

[i] No Config Backups Found.

[+] Enumerating DB Exports (via Passive and Aggressive Methods)
 Checking DB Exports - Time: 00:00:00 <==========================> (71 / 71) 100.00% Time: 00:00:00

[i] No DB Exports Found.

[+] Enumerating Medias (via Passive and Aggressive Methods) (Permalink setting must be set to "Plain" for those to be detected)
 Brute Forcing Attachment IDs - Time: 00:00:34 <===============> (100 / 100) 100.00% Time: 00:00:34

[i] No Medias Found.

[+] Enumerating Users (via Passive and Aggressive Methods)
 Brute Forcing Author IDs - Time: 00:00:05 <=====================> (10 / 10) 100.00% Time: 00:00:05

[i] User(s) Identified:

[+] admin
 | Found By: Rss Generator (Passive Detection)
 | Confirmed By:
 |  Wp Json Api (Aggressive Detection)
 |   - http://10.10.10.29/wordpress/index.php/wp-json/wp/v2/users/?per_page=100&page=1
 |  Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 |  Login Error Messages (Aggressive Detection)

```