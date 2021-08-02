went through usual priv esc enum methods without luck.

ran linpeas.sh

found that we were in the `lxd` group

knowing this we can use lxc/lxd group priv esc

I followed method 1 on this article:

https://book.hacktricks.xyz/linux-unix/privilege-escalation/interesting-groups-linux-pe/lxd-privilege-escalation

things to note when following this method:
 - make sure you're in right directory when saving the alpine.yaml file
 - remember to be in the $home directory on the victim machine when pulling `lxd.tar.xz` and `rootfs.squashfs`
 - don't forget to mount the file system in /mnt/root
 	`lxc config device add privesc host-root disk source=/ path=/mnt/root recursive=true`
	
	
Once you have root, don't forget you mounted the filesystem to `/mnt/root/`

You can find the flag in `/mnt/root/root`
	
	
	