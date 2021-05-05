rustscan --ulimit 5000 -a 10.200.84.200 -r 1-15000 -- -A 

```bash

Open 10.200.84.200:22
Open 10.200.84.200:80
Open 10.200.84.200:443
Open 10.200.84.200:10000


PORT      STATE SERVICE  REASON  VERSION
22/tcp    open  ssh      syn-ack OpenSSH 8.0 (protocol 2.0)
| ssh-hostkey: 
|   3072 9c:1b:d4:b4:05:4d:88:99:ce:09:1f:c1:15:6a:d4:7e (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDfKbbFLiRV9dqsrYQifAghp85qmXpYEHf2g4JJqDKUL316TcAoGj62aamfhx5isIJHtQsA0hVmzD+4pVH4r8ANkuIIRs6j9cnBrLGpjk8xz9+BE1Vvd8lmORGxCqTv+9LgrpB7tcfoEkIOSG7zeY182kOR72igUERpy0JkzxJm2gIGb7Caz1s5/ScHEOhGX8VhNT4clOhDc9dLePRQvRooicIsENqQsLckE0eJB7rTSxemWduL+twySqtwN80a7pRzS7dzR4f6fkhVBAhYflJBW3iZ46zOItZcwT2u0wReCrFzxvDxEOewH7YHFpvOvb+Exuf3W6OuSjCHF64S7iU6z92aINNf+dSROACXbmGnBhTlGaV57brOXzujsWDylivWZ7CVVj1gB6mrNfEpBNE983qZskyVk4eTNT5cUD+3I/IPOz1bOtOWiraZCevFYaQR5AxNmx8sDIgo1z4VcxOMhrczc7RC/s3KWcoIkI2cI5+KUnDtaOfUClXPBCgYE50=
|   256 93:55:b4:d9:8b:70:ae:8e:95:0d:c2:b6:d2:03:89:a4 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBFccvYHwpGWYUsw9mTk/mEvzyrY4ghhX2D6o3n/upTLFXbhJPV6ls4C8O0wH6TyGq7ClV3XpVa7zevngNoqlwzM=
|   256 f0:61:5a:55:34:9b:b7:b8:3a:46:ca:7d:9f:dc:fa:12 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINLfVtZHSGvCy3JP5GX0Dgzcxz+Y9In0TcQc3vhvMXCP
80/tcp    open  http     syn-ack Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1c)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1c
|_http-title: Did not follow redirect to https://thomaswreath.thm
443/tcp   open  ssl/http syn-ack Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1c)
| http-methods: 
|   Supported Methods: POST OPTIONS HEAD GET TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1c
|_http-title: Thomas Wreath | Developer
| ssl-cert: Subject: commonName=thomaswreath.thm/organizationName=Thomas Wreath Development/stateOrProvinceName=East Riding Yorkshire/countryName=GB/emailAddress=me@thomaswreath.thm/localityName=Easingwold
| Issuer: commonName=thomaswreath.thm/organizationName=Thomas Wreath Development/stateOrProvinceName=East Riding Yorkshire/countryName=GB/emailAddress=me@thomaswreath.thm/localityName=Easingwold
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-05-05T19:34:13
| Not valid after:  2022-05-05T19:34:13
| MD5:   fed9 bf4b b9bc fd7b e92e 9eaf b585 8ccb
| SHA-1: 35b7 2d74 7a7b 17d0 aac8 ae47 624f 2059 d438 6b9f
| -----BEGIN CERTIFICATE-----
| MIIELTCCAxWgAwIBAgIUNxH95bFOMXgZR1OriE1iQpHHdKIwDQYJKoZIhvcNAQEL
| BQAwgaUxCzAJBgNVBAYTAkdCMR4wHAYDVQQIDBVFYXN0IFJpZGluZyBZb3Jrc2hp
| cmUxEzARBgNVBAcMCkVhc2luZ3dvbGQxIjAgBgNVBAoMGVRob21hcyBXcmVhdGgg
| RGV2ZWxvcG1lbnQxGTAXBgNVBAMMEHRob21hc3dyZWF0aC50aG0xIjAgBgkqhkiG
| 9w0BCQEWE21lQHRob21hc3dyZWF0aC50aG0wHhcNMjEwNTA1MTkzNDEzWhcNMjIw
| NTA1MTkzNDEzWjCBpTELMAkGA1UEBhMCR0IxHjAcBgNVBAgMFUVhc3QgUmlkaW5n
| IFlvcmtzaGlyZTETMBEGA1UEBwwKRWFzaW5nd29sZDEiMCAGA1UECgwZVGhvbWFz
| IFdyZWF0aCBEZXZlbG9wbWVudDEZMBcGA1UEAwwQdGhvbWFzd3JlYXRoLnRobTEi
| MCAGCSqGSIb3DQEJARYTbWVAdGhvbWFzd3JlYXRoLnRobTCCASIwDQYJKoZIhvcN
| AQEBBQADggEPADCCAQoCggEBALgQ9Z4iCgX5ryzu6/9T/3SLVsPOqxxy9iH2uZkL
| P35sCCZsov+4Z/A10z9VBn/ZiEwNu2Te5LALAijAvCqbylCFtJy726KbW5pjwy3+
| kz2/T9YpxhugmIVPAHVrdP8KMf6T7yVQLsDt+19s6L8x238lSv3Nv9weikBUKX0a
| 6sT62PSf4wlVMbrqXuuJeyBewJYMq3lChqo9CFJxaA1uvcIi7aUDx1wi4jUJZ3wa
| aho5A0id+lg7L+OGxO6J7JhVbZP6EGq8HSa6Xitb3Y00NhS001qLLSNAaoYh+rKT
| mPESyaGEa0BoPEWK50j57Nwwl/kJwPZcp0ZrhdrNMWZPvzsCAwEAAaNTMFEwHQYD
| VR0OBBYEFJ0QlPD2WLjDO5qJPGiRqr86eodEMB8GA1UdIwQYMBaAFJ0QlPD2WLjD
| O5qJPGiRqr86eodEMA8GA1UdEwEB/wQFMAMBAf8wDQYJKoZIhvcNAQELBQADggEB
| AKMCMIZUFVinVny9L+S420dj5T+StcHH8ogR992udkT6BYlcchc9owGtPnVXaWP3
| xw2Rz3pKiKrSyBVms6JKbacNP5ksmZP58KYzN16rBd1Ubzpjmn6JX8KBJ3Z+HUE6
| qZleksAps18fgrSz7HEIU0oOQYL/wk82I75IER4pBzVO/ktVt0u0mk1zAe0H8bJ2
| y6Yh1EkR3y3SUxEiuwkfrw3i/MxH53nvZGJA+7Va1lXVyiblzAYk80QpKjJ894ib
| 5KAzre3nqVZiwxpmnpx9z5l27zZD5UzDFd1U00enGkLU3Q5IxYSHcw+LyVx6oH4J
| nDesZWShhdPS9Ui7VvN4o8o=
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  http/1.1
10000/tcp open  http     syn-ack MiniServ 1.890 (Webmin httpd)
|_http-favicon: Unknown favicon MD5: 8E8E99E610C1F8474422D68A4D749607
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Site doesn't have a title (text/html; Charset=iso-8859-1).
```
