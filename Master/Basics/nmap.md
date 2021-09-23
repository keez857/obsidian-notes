`-Pn` will disable pings, this is useful for boxes that aren't accepting ICMP traffic. This often happens with Windows, or if you're using proxychains.

---

### udp scan
`nmap -sU 10.10.10.55 --top-ports 100`

