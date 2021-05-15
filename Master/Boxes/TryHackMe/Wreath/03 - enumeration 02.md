There are five possible ways to enumerate a network through a compromised host (in order of preference):

```
1.  Using material found on the machine. The hosts file or ARP cache, for example   
2.  Using pre-installed tools     
3.  Using statically compiled tools
4.  Using scripting techniques
5.  Using local tools through a proxy
```

---

### Some steps we can take:

`arp -a` checking the arp cache we can see other machines the target has interacted with

`/etc/hosts/`
`C:\Windows\System32\drivers\etc\host`
We can check static mappings

`/etc/resolv.conf` or `nmcli dev show`
Will identify any local DNS servers

---

### Network scanning through compromised host

Bash ping sweep one-liner for /24 network
```bash
for i in {1..255}; do (ping -c 1 192.168.1.${i} | grep "bytes from" &); done
```

---


We first download a static nmap binary on our attack box and host the file.

We download the binary from the compromised machine and save it as /tmp/nmap-k

We can now use the bianry to scan the network for other hosts using this command:
`./nmap-k -sn 10.200.84.1-255 -oN scan-keez`

We can see these hosts:
```
10.200.84.1
10.200.84.100
10.200.84.150
10.200.84.200
10.200.84.250
```

**.1** and **.250 **are out of scope. \
**.200 **we have compromised.\
This leaves us with** .100 **and **.150**

---

On the compromised box **.200,** we run an nmap scan on **.150**

`./nmap-k -p 1-15000 10.200.84.150`


```bash
80/tcp   open  http
135/tcp  open  epmap
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-wbt-server
5985/tcp open  wsman
```



