we can connect to redis DB with this command
```
redis-cli -h 10.10.117.165 -a B65Hx562F@ggAZ@F
```

---
redis-cli commands

`keys *` list all keys

This gets us the following list:
```
10.10.117.165:6379> keys *
1) "tmp"
2) "internal flag"
3) "int"
4) "marketlist"
5) "authlist"
```

We can grab the internal flag:
```
mget "internal flag"
```


---

We have to run the `lrange` command to view the `authlist` key

This reveals:

```
Authorization for rsync://rsync-connect@127.0.0.1 with password Hcg3HP67@TW@Bc72v
```

