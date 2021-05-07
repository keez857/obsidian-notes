## __***Easy way***__
Open up a listening port on the compromised box, redirect traffic that comes into compromised box to the target server.

**Compromised Server**: 172.16.0.5
**Target**: 172.16.0.10 port 3306

`./socat tcp-l:33060,fork,reuseaddr tcp:172.16.0.10:3306 &`

This opens port 33060 on compromised box and redirects input from attacking machine to target server.

`fork` - puts every connection into a new process\
`reuseaddr` - port stays open after a connection is made to it\
`&` - backgrounds the shell

Combined, this allows us to use same port forward for more than one connection

---

## *Quiet way*
