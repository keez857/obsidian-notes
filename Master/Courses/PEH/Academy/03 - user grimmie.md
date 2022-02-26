I browsed around and found two things of note.

`/var/www/html/academy/includes/config.php`

has creds

```
$mysql_hostname = "localhost";
$mysql_user = "grimmie";
$mysql_password = "My_V3ryS3cur3_P4ss";
$mysql_database = "onlinecourse";
$bd = mysqli_connect($mysql_hostname, $mysql_user, $mysql_password, $mysql_database) or die("Could not connect database");
```

We can log into the phpmyadmin portal @ `http://academy.tcm/phpmyadmin`

`grimmie:My_V3ryS3cur3_P4ss`

We also read in the note earlier that grimmie reuses their pw.

I tried logging into SSH with the same creds and was successful

---

onlinecourse.sql can be found here:

`/var/www/html/academy/db/onlinecourse.sql`

