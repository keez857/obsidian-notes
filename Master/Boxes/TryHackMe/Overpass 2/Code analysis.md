We first make our way to the github repo we found in the TCP stream

https://github.com/NinjaJc01

We find the answer to Q1 on line 19 in `main.go`

`bdd04d9bb7621687f5df9001f5098eb22bf19eac4c2c30b6f23efed4d24807277d0f8bfccb9e77659103d78c56e66d2d7d8391dfc885d0e9b68acd01fc2170e3`


The hash is found at the bottom:

`1c362db832f3f864c8c2fe05f2002a05`

We create a crackable txt file with the hash and salt:

`6d05358f090eea56a238af02e47d44ee5489d234810ef6240280857ec69712a3e5e370b8a41899d0196ade16c0d54327c5654019292cbfe0b5e98ad1fec71bed:1c362db832f3f864c8c2fe05f2002a05`

Then we use hashcat to crack it:

`hashcat -a 0 -m 1710 crackme.txt /usr/share/wordlists/rockyou.txt 
`
