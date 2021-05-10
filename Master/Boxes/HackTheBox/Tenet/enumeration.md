First thing I did was edit /etc/hosts to include:
```
10.10.10.223	tenet.htb
```

---

http://tenet.htb/index.php/2020/12/16/logs/#comment-2
Reveals the following message:
```
did you remove the sator php file and the backup?? the migration program is incomplete! why would you do this?!
```

There is some text at http://10.10.10.223/sator.php
```
[+] Grabbing users from text file  
[] Database updated
```

Because the comment mentioned a backup, we can try
http://10.10.10.223/sator.php.bak **(needed a hint for this)**
This allows us to download the .bak file

File contents:
```php
<?php

class DatabaseExport
{
        public $user_file = 'users.txt';
        public $data = '';

        public function update_db()
        {
                echo '[+] Grabbing users from text file <br>';
                $this-> data = 'Success';
        }


        public function __destruct()
        {
                file_put_contents(__DIR__ . '/' . $this ->user_file, $this->data);
                echo '[] Database updated <br>';
        //      echo 'Gotta get this working properly...';
        }
}

$input = $_GET['arepo'] ?? '';
$databaseupdate = unserialize($input);

$app = new DatabaseExport;
$app -> update_db();


?>
```

---

We have also found 2 usernames from wpscan:
**neil**
**protagonist**

---

wpscan tells us xmlrpc is enabled which means we can brute force
Perform a wpscan brute force attack with the two usernames
`wpscan --url tenet.htb -U neil,protagonist -=passwords /usr/share/wordlists/rockyou.txt`

**NO RESULTS**