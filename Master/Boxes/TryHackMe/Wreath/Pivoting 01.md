We first download a static nmap binary on our attack box and host the file.

We download the binary from the compromised machine and save it as /tmp/nmap-k

We can now use the bianry to scan the network for other hosts using this command:
`./nmap-k -sn 10.200.84.1-255 -oN scan-keez`

We can see these hosts:
```
