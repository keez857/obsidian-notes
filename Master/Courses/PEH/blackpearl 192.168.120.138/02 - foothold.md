going to any 404 page reveals the webserver is using `nginx/1.14.2`

we can also see that in view-source: `webmaster: alek@blackpearl.tcm`

We find a `/secret` directory that tells us that dir busting will not work

We move onto enumerating port 53 dns

It is using Bind 9 ISC. This is one of the oldest solutions
`ISC BIND 9.11.5-P4-5.1+deb10u5`


We can look for ISC Bind vulnerabilities for this version


---

## dnsrecon

originally in the /etc/hosts file I set the ip to `black.tcm` 

this was a mistake

Since we know there is DNS running on the box, we run dnsrecon and see that there is a record for `blackpearl.tcm`

If we change the /etc/hosts file for the ip to point to `blackpearl.tcm`  instead, we get what we need. 