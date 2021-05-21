Local port forward is where we connect from our own attacking machine to a chisel server listening on a compromised box.

On the compromised box we set up a chisel server:
`./chisel server -p LISTEN_PORT`

We connect from our attack box:
`./chisel client LISTEN_IP:LISTEN_PORT LOCAL_PORT:TARGET_IP:TARGET_PORT`

---

### example
target: 172.16.0.10:**22**
compromised: 172.16.0.5:**8000**

Run command on attack box to forward local port **2222** to our target:\
`./chisel client 172.16.0.5:8000 2222:172.16.0.10:22`


