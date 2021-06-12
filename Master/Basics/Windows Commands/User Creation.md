First we create the account itself:  
`net user USERNAME PASSWORD /add`  


Next we add our newly created account in the "Administrators" and "Remote Management Users" groups:  
`net localgroup Administrators USERNAME /add  
net localgroup "Remote Management Users" USERNAME /add`