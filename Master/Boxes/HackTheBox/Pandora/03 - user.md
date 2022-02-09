Once we have access to the web gui we can simply go to

`admin tools > extension manager > extension uploader`

We cannot simply upload a php rev shell. We throw it into a zip file and upload the zip file

We can then access the rev shell in `http://localhost:9090/pandora_console/extensions/`

---

Once we stabalize our shell, use `ssh-keygen` to create the `.ssh` folder and create an `authorized_keys` file with 0600 perms. 

Add our id_rsa.pub

