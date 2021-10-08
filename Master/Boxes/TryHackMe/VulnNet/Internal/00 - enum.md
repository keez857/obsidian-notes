### nmap

```
nmap -A 10.10.117.165
Starting Nmap 7.91 ( https://nmap.org ) at 2021-10-07 22:38 EDT
Nmap scan report for 10.10.117.165
Host is up (0.19s latency).
Not shown: 993 closed ports
PORT     STATE    SERVICE     VERSION
22/tcp   open     ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 5e:27:8f:48:ae:2f:f8:89:bb:89:13:e3:9a:fd:63:40 (RSA)
|   256 f4:fe:0b:e2:5c:88:b5:63:13:85:50:dd:d5:86:ab:bd (ECDSA)
|_  256 82:ea:48:85:f0:2a:23:7e:0e:a9:d9:14:0a:60:2f:ad (ED25519)
111/tcp  open     rpcbind     2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      36615/tcp   mountd
|   100005  1,2,3      38196/udp   mountd
|   100005  1,2,3      42869/tcp6  mountd
|   100005  1,2,3      51232/udp6  mountd
|   100021  1,3,4      38579/udp6  nlockmgr
|   100021  1,3,4      39551/tcp6  nlockmgr
|   100021  1,3,4      43421/tcp   nlockmgr
|   100021  1,3,4      46193/udp   nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl                                                                     
139/tcp  open     netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)                                      
445/tcp  open     netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)                                   
873/tcp  open     rsync       (protocol version 31)                                                            
2049/tcp open     nfs_acl     3 (RPC #100227)                                                                  
9090/tcp filtered zeus-admin                                                                                   
Service Info: Host: VULNNET-INTERNAL; OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

---

### nmap v2

```
nmap -p- -Pn 10.10.117.165
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-10-07 23:56 EDT
Nmap scan report for 10.10.117.165
Host is up (0.18s latency).
Not shown: 65523 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
111/tcp   open     rpcbind
139/tcp   open     netbios-ssn
445/tcp   open     microsoft-ds
873/tcp   open     rsync
2049/tcp  open     nfs
6379/tcp  open     redis
9090/tcp  filtered zeus-admin
36615/tcp open     unknown
36983/tcp open     unknown
43421/tcp open     unknown
50045/tcp open     unknown
```
