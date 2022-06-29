## nmap
```
nmap -p53,139,135,445,464,6379,9389 -sV -sC -T4 -Pn 10.10.55.49
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2022-06-24 15:53 EDT
Nmap scan report for active.thm (10.10.55.49)
Host is up (0.18s latency).

PORT     STATE SERVICE       VERSION
53/tcp   open  domain        Simple DNS Plus
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds?
464/tcp  open  kpasswd5?
6379/tcp open  redis         Redis key-value store 2.8.2402
9389/tcp open  mc-nmf        .NET Message Framing
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2022-06-24T19:53:39
|_  start_date: N/A


```

---

## enum4linux
```
Domain Name: VULNNET                                                                                        
Domain Sid: S-1-5-21-1405206085-1650434706-76331420


```

---


## redis-cli

First connect to redis with
```
redis-cli -h <ip address>
```

We can grab config info
```
CONFIG GET *
```

```
1) "dbfilename"
  2) "dump.rdb"
  3) "requirepass"
  4) ""
  5) "masterauth"
  6) ""
  7) "unixsocket"
  8) ""
  9) "logfile"
 10) ""
 11) "pidfile"
 12) "/var/run/redis.pid"
 13) "maxmemory"
 14) "0"
 15) "maxmemory-samples"
 16) "3"
 17) "timeout"
 18) "0"
 19) "tcp-keepalive"
 20) "0"
 21) "auto-aof-rewrite-percentage"
 22) "100"
 23) "auto-aof-rewrite-min-size"
 24) "67108864"
 25) "hash-max-ziplist-entries"
 26) "512"
 27) "hash-max-ziplist-value"
 28) "64"
 29) "list-max-ziplist-entries"
 30) "512"
 31) "list-max-ziplist-value"
 32) "64"
 33) "set-max-intset-entries"
 34) "512"
 35) "zset-max-ziplist-entries"
 36) "128"
 37) "zset-max-ziplist-value"
 38) "64"
 39) "hll-sparse-max-bytes"
 40) "3000"
 41) "lua-time-limit"
 42) "5000"
 43) "slowlog-log-slower-than"
 44) "10000"
 45) "latency-monitor-threshold"
 46) "0"
 47) "slowlog-max-len"
 48) "128"
 49) "port"
 50) "6379"
 51) "tcp-backlog"
 52) "511"
 53) "databases"
 54) "16"
 55) "repl-ping-slave-period"
 56) "10"
 57) "repl-timeout"
 58) "60"
 59) "repl-backlog-size"
 60) "1048576"
 61) "repl-backlog-ttl"
 62) "3600"
 63) "maxclients"
 64) "10000"
 65) "watchdog-period"
 66) "0"
 67) "slave-priority"
 68) "100"
 69) "min-slaves-to-write"
 70) "0"
 71) "min-slaves-max-lag"
 72) "10"
 73) "hz"
 74) "10"
 75) "repl-diskless-sync-delay"
 76) "5"
 77) "no-appendfsync-on-rewrite"
 78) "no"
 79) "slave-serve-stale-data"
 80) "yes"
 81) "slave-read-only"
 82) "yes"
 83) "stop-writes-on-bgsave-error"
 84) "yes"
 85) "daemonize"
 86) "no"
 87) "rdbcompression"
 88) "yes"
 89) "rdbchecksum"
 90) "yes"
 91) "activerehashing"
 92) "yes"
 93) "repl-disable-tcp-nodelay"
 94) "no"
 95) "repl-diskless-sync"
 96) "no"
 97) "aof-rewrite-incremental-fsync"
 98) "yes"
 99) "aof-load-truncated"
100) "yes"
101) "appendonly"
102) "no"
103) "dir"
104) "C:\\Users\\enterprise-security\\Downloads\\Redis-x64-2.8.2402"
105) "maxmemory-policy"
106) "volatile-lru"
107) "appendfsync"
108) "everysec"
109) "save"
110) "jd 3600 jd 300 jd 60"
111) "loglevel"
112) "notice"
113) "client-output-buffer-limit"
114) "normal 0 0 0 slave 268435456 67108864 60 pubsub 33554432 8388608 60"
115) "unixsocketperm"
116) "0"
117) "slaveof"
118) ""
119) "notify-keyspace-events"
120) ""
121) "bind"
122) ""

```

We can see that `enterprise-security` is a user

## impacket-rpcdump
```
impacket-rpcdump active.thm | grep "Protocol\: \["
Protocol: [MS-RSP]: Remote Shutdown Protocol 
Protocol: [MS-EVEN6]: EventLog Remoting Protocol 
Protocol: [MS-TSCH]: Task Scheduler Service Remoting Protocol 
Protocol: [MS-TSCH]: Task Scheduler Service Remoting Protocol 
Protocol: [MS-TSCH]: Task Scheduler Service Remoting Protocol 
Protocol: [MS-NRPC]: Netlogon Remote Protocol 
Protocol: [MS-RAA]: Remote Authorization API Protocol 
Protocol: [MS-SAMR]: Security Account Manager (SAM) Remote Protocol 
Protocol: [MS-LSAT]: Local Security Authority (Translation Methods) Remote 
Protocol: [MS-FRS2]: Distributed File System Replication Protocol 
Protocol: [MS-CMPO]: MSDTC Connection Manager: 
Protocol: [MS-DNSP]: Domain Name Service (DNS) Server Management 
Protocol: [MS-SCMR]: Service Control Manager Remote Protocol 
Protocol: [MS-RPRN]: Print System Remote Protocol 
Protocol: [MS-PAN]: Print System Asynchronous Notification Protocol 
Protocol: [MS-PAN]: Print System Asynchronous Notification Protocol 
Protocol: [MS-PAR]: Print System Asynchronous Remote Protocol 
Protocol: [MS-DRSR]: Directory Replication Service (DRS) Remote Protocol 
```

