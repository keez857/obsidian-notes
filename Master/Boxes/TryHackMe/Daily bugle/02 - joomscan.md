Tribal knowledge - we can use joomscan which is native to Kali to enumerate further

`joomscan -u <ip address>`

```bash
[+] FireWall Detector
[++] Firewall not detected

[+] Detecting Joomla Version
[++] Joomla 3.7.0

[+] Core Joomla Vulnerability
[++] Target Joomla core is not vulnerable

[+] Checking Directory Listing
[++] directory has directory listing : 
http://10.10.206.115/administrator/components
http://10.10.206.115/administrator/modules
http://10.10.206.115/administrator/templates
http://10.10.206.115/images/banners


[+] Checking apache info/status files
[++] Readable info/status files are not found

[+] admin finder
[++] Admin page : http://10.10.206.115/administrator/

[+] Checking robots.txt existing
[++] robots.txt is found
path : http://10.10.206.115/robots.txt 

Interesting path found from robots.txt
http://10.10.206.115/joomla/administrator/
http://10.10.206.115/administrator/
http://10.10.206.115/bin/                                                                       
http://10.10.206.115/cache/                                                                     
http://10.10.206.115/cli/                                                                       
http://10.10.206.115/components/                                                                
http://10.10.206.115/includes/                                                                  
http://10.10.206.115/installation/                                                              
http://10.10.206.115/language/                                                                  
http://10.10.206.115/layouts/                                                                   
http://10.10.206.115/libraries/                                                                 
http://10.10.206.115/logs/                                                                      
http://10.10.206.115/modules/                                                                   
http://10.10.206.115/plugins/                                                                   
http://10.10.206.115/tmp/                                                                       
                                                                                                
                                                                                                
[+] Finding common backup files name                                                            
[++] Backup files are not found                                                                 
                                                                                                
[+] Finding common log files name                                                               
[++] error log is not found                                                                     
                                                                                                
[+] Checking sensitive config.php.x file                                                        
[++] Readable config files are not found  
```