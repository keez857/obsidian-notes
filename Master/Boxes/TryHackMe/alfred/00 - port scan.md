```rust
80/tcp   open  http               syn-ack Microsoft IIS httpd 7.5
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/7.5
|_http-title: Site doesn't have a title (text/html).
3389/tcp open  ssl/ms-wbt-server? syn-ack
| ssl-cert: Subject: commonName=alfred
| Issuer: commonName=alfred
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2021-05-14T02:07:57
| Not valid after:  2021-11-13T02:07:57
| MD5:   c3e1 0931 d05e cd79 52bc ef39 efb3 31ba
| SHA-1: 31e9 1e54 72ea e4a8 b5a4 3a63 26dc c9d9 450d 1aeb
| -----BEGIN CERTIFICATE-----
| MIIC0DCCAbigAwIBAgIQF3oHM1XzhKBJs2F1IZCvwjANBgkqhkiG9w0BAQUFADAR
| MQ8wDQYDVQQDEwZhbGZyZWQwHhcNMjEwNTE0MDIwNzU3WhcNMjExMTEzMDIwNzU3
| WjARMQ8wDQYDVQQDEwZhbGZyZWQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
| AoIBAQCgHzh2R+3vIxr27DZCjoFkUvB0ifvS7zikwa09B88lmsiQ30FTNbRQp6Fj
| dtbSqS0veshnE0KPr83I2GbwZIgT+OdwyuXUofKCoZdWadnqiEf9DIXGVkGoxE7Z
| kKfds4rQTJVhcnZ8jKJ7gkaxFr1yy6bsJV+CoM9CJocT8c+NFN8UUeyzmFDUdO6i
| peAO+v3zdq2xHM1S5csN+qnSSuWXuJuQngTdJiVbcK6ROOti/avqSU1vN+Az71K8
| rmwG1u0mC6GlAtjlx4fgQuKlGboD3fOKV9puidD8dFVnw4obd2EhBf+7LyyCn4zQ
| JPt/SR0v2NoeEeN5f95Av7TEpc8/AgMBAAGjJDAiMBMGA1UdJQQMMAoGCCsGAQUF
| BwMBMAsGA1UdDwQEAwIEMDANBgkqhkiG9w0BAQUFAAOCAQEANsVnqRfe8jaNMouM
| GD3L/xJWNHOKeftFreDXmuTOMHf11sekpxT+tBZpRPY0TQjZDXT2kLaLYdzVFdzX
| g28uWUu/inVQsNbyI7jj3SH4T4jOJoasmGA6efvL2YqyEMcTvz3QUEmmAp5XRPNp
| J62f8d2iOGQrAtffAylnItHqsJYK9UBHjKBVHQvzXJrtiFT6ADCUe6srzWasepvy
| Ur4UH5J57QhsCyF98JpGOf7rrij2h7C7JaDXQwBuKNdnb47QopLqL+4STjTczgUI
| 2OB8yxwJmP1MkER2EquBOOL56sN9WuoaEgZlL+k4Ds3v+J8I2Y4wcZTK1LQ/GaMP
| s9w3PQ==
|_-----END CERTIFICATE-----
|_ssl-date: 2021-05-15T02:11:10+00:00; 0s from scanner time.
8080/tcp open  http               syn-ack Jetty 9.4.z-SNAPSHOT
|_http-favicon: Unknown favicon MD5: 23E8C7BD78E8CD826C5A6073B15068B1
| http-robots.txt: 1 disallowed entry 
|_/
|_http-server-header: Jetty(9.4.z-SNAPSHOT)
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```