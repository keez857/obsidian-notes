## subdomains
`gobuster dns -d mysite.com -t 50 -w subdomains.txt`

---

## vhosts
`gobuster vhost -u mysite.com -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt -k -r -t 25