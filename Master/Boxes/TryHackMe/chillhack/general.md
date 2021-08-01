    gobuster revealed /secret directory  
  
sudo -l reveals user can run  

## /home/apaar/.helpline.sh

  
  
  
using tac (thanks gopro) we can read the script  
  
```bash
#!/bin/bash  
  
echo  
echo "Welcome to helpdesk. Feel free to talk to anyone at any time!"  
echo  
  
read -p "Enter the person whom you want to talk with: " person  
read -p "Hello user! I am $person, Please enter your message: " msg  
  
$msg 2>/dev/null  
```

cannot use ls to view file perms, used ‘stat’ command to view perms on

### /home/apaar/.helpline.sh

  
  
  
able to exec commoands with **echo \`**_**command**_**\`**  
used this to curl a bash rev shell script from attacker pc  
  
gained shell for www-data  
  
we were able to exec commands as apaar using helpline.sh (second line of input)  
  
netstat reveals port 9001 open for mysql  
  
connected to mysql db and enumerated passwords for Aurick and cullapaar  
  
  
  
aurick: 7e53614ced3640d5de23f111806cc4fd  
cullapaar: 686216240ed5af30df0501e53c789a649  
  
  
Anurodh  
!d0ntKn0wmYp@ssw0rd