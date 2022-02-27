# 192.168.120.136

## nmap

```
PORT      STATE SERVICE  VERSION
22/tcp    open  ssh      OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 bd:96:ec:08:2f:b1:ea:06:ca:fc:46:8a:7e:8a:e3:55 (RSA)
|   256 56:32:3b:9f:48:2d:e0:7e:1b:df:20:f8:03:60:56:5e (ECDSA)
|_  256 95:dd:20:ee:6f:01:b6:e1:43:2e:3c:f4:38:03:5b:36 (ED25519)
80/tcp    open  http     Apache httpd 2.4.38 ((Debian))
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: Bolt - Installation error
111/tcp   open  rpcbind  2-4 (RPC #100000)
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
|   100005  1,2,3      36608/udp6  mountd
|   100005  1,2,3      54077/udp   mountd
|   100005  1,2,3      58721/tcp6  mountd
|   100005  1,2,3      59899/tcp   mountd
|   100021  1,3,4      37290/udp   nlockmgr
|   100021  1,3,4      39367/tcp6  nlockmgr
|   100021  1,3,4      41047/tcp   nlockmgr
|   100021  1,3,4      56556/udp6  nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp  open  nfs_acl  3 (RPC #100227)
8080/tcp  open  http     Apache httpd 2.4.38 ((Debian))
|_http-open-proxy: Proxy might be redirecting requests
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: PHP 7.3.27-1~deb10u1 - phpinfo()
41047/tcp open  nlockmgr 1-4 (RPC #100021)
48377/tcp open  mountd   1-3 (RPC #100005)
53437/tcp open  mountd   1-3 (RPC #100005)
59899/tcp open  mountd   1-3 (RPC #100005)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```


## gobuster http 80
```
/public               (Status: 301) [Size: 303] [--> http://dev.tcm/public/]
/src                  (Status: 301) [Size: 300] [--> http://dev.tcm/src/]   
/app                  (Status: 301) [Size: 300] [--> http://dev.tcm/app/]   
/vendor               (Status: 301) [Size: 303] [--> http://dev.tcm/vendor/]
/extensions           (Status: 301) [Size: 307] [--> http://dev.tcm/extensions/]
/server-status        (Status: 403) [Size: 272] 
```


## gobuster http 8080

```
/dev                  (Status: 301) [Size: 307] [--> http://dev.tcm:8080/dev/]
/server-status        (Status: 403) [Size: 274] 
```