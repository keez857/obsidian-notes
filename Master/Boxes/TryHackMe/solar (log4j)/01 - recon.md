```
map -sC -sV 10.10.43.212                                                                               
Starting Nmap 7.91 ( https://nmap.org ) at 2021-12-14 12:50 EST
Nmap scan report for 10.10.43.212
Host is up (0.18s latency).
Not shown: 998 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e2:35:e1:4f:4e:87:45:9e:5f:2c:97:e0:da:a9:df:d5 (RSA)
|   256 b2:fd:9b:75:1c:9e:80:19:5d:13:4e:8d:a0:83:7b:f9 (ECDSA)
|_  256 75:20:0b:43:14:a9:8a:49:1a:d9:29:33:e1:b9:1a:b6 (ED25519)
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|_  100000  3,4          111/udp6  rpcbind
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 20.78 seconds
┌─[keez@10.13.22.125:~/boxes/thm/solar]
└─╼ nmap -sC -sV -p8983 10.10.43.212                                                                        
Starting Nmap 7.91 ( https://nmap.org ) at 2021-12-14 12:50 EST
Nmap scan report for 10.10.43.212
Host is up (0.18s latency).

PORT     STATE SERVICE VERSION
8983/tcp open  http    Apache Solr
| http-title: Solr Admin
|_Requested resource was http://10.10.43.212:8983/solr/

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.71 seconds
```
