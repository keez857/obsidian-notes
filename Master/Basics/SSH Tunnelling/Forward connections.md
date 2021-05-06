This technique is more commonly used against Unix hosts which commonly have ssh port open.

Port forwarding is used with `-L` switch which creates a link to a LOCAL port

## example
We have SSH access to **172.16.0.5**
There is a webserver on **172.16.0.10**
We use the following command to create a link to the webserver:

`ssh -L 8000:172.16.0.10:80 user@172.16.0.5 -fN`
<font size="2"> (note: `-f` backgrounds the shell. `-N` tells SSH it doesn't need to exec any commands -- only set up the connection) </font>


We could then access the website on 172.16.0.10 (through 172.16.0.5) by navigating to port 8000 _on our own_ _attacking machine._

We can do this by entering `localhost:8000` into a web browser 

---


**Proxies** are made using the `-D` switch, for example: `-D 1337`. 

This will open up port 1337 on your attacking box as a proxy to send data through into the protected network. This is useful when combined with a tool such as proxychains. An example of this command would be:  

`ssh -D 1337 user@172.16.0.5 -fN`

