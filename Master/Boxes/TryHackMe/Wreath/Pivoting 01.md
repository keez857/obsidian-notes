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

See [[enumeration 03]]

---

We can use sshuttle to create a tunnel to our next target @ **10.200.84.150:80**

`sshuttle -r root@10.200.84.200 --ssh-cmd "ssh -i id_rsa" 10.200.84.0/24`

We can now access http://10.200.84.150

This page reveals that it is running **gitstack**