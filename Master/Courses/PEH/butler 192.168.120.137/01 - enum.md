## nmap

```
nmap -p135,139,445,5040,7680,8080,49664,49665,49666,49667,49668,49670 -sV -sC -T4 -Pn -oA 192.168.120.137 192.168.120.137
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2022-03-04 00:03 EST
Nmap scan report for butler.tcm (192.168.120.137)
Host is up (0.0091s latency).

PORT      STATE SERVICE       VERSION
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds?
5040/tcp  open  unknown
7680/tcp  open  pando-pub?
8080/tcp  open  http          Jetty 9.4.41.v20210516
| http-robots.txt: 1 disallowed entry 
|_/
|_http-server-header: Jetty(9.4.41.v20210516)
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
49670/tcp open  msrpc         Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 59m59s
|_nbstat: NetBIOS name: BUTLER, NetBIOS user: <unknown>, NetBIOS MAC: 00:0c:29:85:3c:4c (VMware)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2022-03-04T06:06:10
|_  start_date: N/A
```


## gobuster on 8080

```
/login                (Status: 200) [Size: 2028]
/assets               (Status: 302) [Size: 0] [--> http://butler.tcm:8080/assets/]
/logout               (Status: 302) [Size: 0] [--> http://butler.tcm:8080/]       
/signup               (Status: 404) [Size: 8275]                                  
/error                (Status: 400) [Size: 6241]                                  
/git                  (Status: 302) [Size: 0] [--> http://butler.tcm:8080/git/]   
/oops                 (Status: 200) [Size: 6503]                                  
/cli                  (Status: 302) [Size: 0] [--> http://butler.tcm:8080/cli/]   
```
