when we go to `secret.htb/docs` it shows us how to register a user and login

Example request:
```
POST /api/user/register HTTP/1.1
Host: secret.htb:3000
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.87 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-GPC: 1
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
If-None-Match: W/"5d-ArPF0JBxjtRzy3wpSVF4hSVtK4s"
Connection: close
Content-Length: 79
Content-Type: application/json

{
"name": "adminn",
	"email": "asdf@adsf.com",
	"password": "password"
 }
```

Be sure to include `content-type`

Our JWT token

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MjBjODU0ZjUzNmUwNTA0NGExM2U0MzAiLCJuYW1lIjoiYWRtaW5uIiwiZW1haWwiOiJhc2RmQGFkc2YuY29tIiwiaWF0IjoxNjQ0OTg4MDcwfQ.2wxXObsM9vGlIcc3TNUQP5T9td9NMyLrN0RRugtO57o
```