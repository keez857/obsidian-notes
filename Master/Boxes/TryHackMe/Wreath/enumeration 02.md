There are five possible ways to enumerate a network through a compromised host (in order of preference):

```
1.  Using material found on the machine. The hosts file or ARP cache, for example   
2.  Using pre-installed tools     
3.  Using statically compiled tools
4.  Using scripting techniques
5.  Using local tools through a proxy
```

### Some steps we can take:

`arp -a` checking the arp cache we can see other machines the target has interacted with

`/etc/hosts/`
`C:\Windows\System32\drivers\etc\host`
We can check static mappings

`/etc/resolv.conf` or `nmcli dev show`
Will identify any local DNS servers


### Network scanning through compromised host

Bash ping sweep one-liner for /24 network
```bash
for i in {1..255}; do (ping -c 1 192.168.1.${i} | grep "bytes from" &); done
```


