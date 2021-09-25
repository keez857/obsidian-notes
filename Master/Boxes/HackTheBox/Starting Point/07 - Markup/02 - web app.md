We can use the creds we exfil'd from the last box to log into the web app
`Daniel:>SNDv*2wzLWf`

Once we are logged in we see there is form submission on the `/services.php` page. Using burpsuite we see this is sent in XML format.

We can google XML injection which leads us to XXE (xml external entity) injection

https://portswigger.net/web-security/xxe


