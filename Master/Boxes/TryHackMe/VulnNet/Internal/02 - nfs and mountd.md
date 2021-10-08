we see that port 2049 is open which is NFS service

by looking this up in hacktricks we find this article:
https://book.hacktricks.xyz/pentesting/nfs-service-pentesting

we use `showmount -e <ip>` to find what folder on the server we can mount to our machine

`/opt/conf` is available

we mount `/opt/conf` to `/mnt/new_temp` on our machine 
```
sudo mount -t nfs <victim_ip>:/opt/conf /mnt/new_temp -o nolock
```

---

Once we have the folder mounted we find
`/mnt/new_temp/redis/redis.conf`

Using this command we can grep out the non commented strings
`grep -oE '^[^#].*' ./redis.conf`

Things of note:
```
requirepass "B65Hx562F@ggAZ@F"
```





