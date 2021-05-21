We need to open up ports on the Windows firewall before we can use a chisel forward proxy

`netsh advfirewall firewall add rule name="keez" dir=in action=allow protocol=tcp localport=4444`

---

Next we will have to create a Chisel SOCKS proxy forward.

We will need to get chisel downloaded on the Windows box then we start the chisel listener

`.\chisel server -p 4444 --socks5`

---

Next we start the Chisel client on our attack box
`./chisel client 10.200.100.150:4444 9090:socks`

We now have a proxy to the personal PC @ 10.200.100.100 and can view the website running on this box by using Foxyproxy SOCKS5 port 9090