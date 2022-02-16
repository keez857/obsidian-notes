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
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MjBjODljM2Q4ZGI1NTA0NGRlZjY0MmYiLCJuYW1lIjoiYWRtaW5uIiwiZW1haWwiOiJhc2RmQGFkc2YuY29tIiwiaWF0IjoxNjQ0OTg4ODk5fQ.5xy6ixmtqXI35ix20TV4x8enAzO7VPM0XFu4ku7QYc4
```



Looked at git commit history

`git diff de0a46b5107a2f4d26e348303e76d85ae4870934 `

We find an old secret:

`gXr67TtoQL8TShUc8XYsK2HvsBYfyQSFCFZe4MQp7gRpFuMkKjcM72CNQN4fMfbZEKx4i7YiWuNAkmuTcdEriCMm9vPAYkhpwPTiuVwVhvwE`


We craft a JWT token with the exact payload dasith used in his docs and sign it with the secret we found (do not check base64 encode)