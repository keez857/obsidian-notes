On the compromised box .200, we run an nmap scan on .150

`./nmap-k -p 1-15000 10.200.84.150`


```bash
80/tcp   open  http
135/tcp  open  epmap
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-wbt-server
5985/tcp open  wsman
```