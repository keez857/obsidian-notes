we can enum the smb shares with
```
smbclient -L //10.10.117.165
```

We see that `shares` is open, we can connect without password

```
smbclient //10.10.117.165/shares
```

we find `services.txt` with our first flag
`THM{0a09d51e488f5fa105d8d866a497440a}`


