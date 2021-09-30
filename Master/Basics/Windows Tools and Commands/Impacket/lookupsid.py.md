This script will help enumerate users and SIDs on windows boxes

SID - security Identifier, unique value identifies user accounts

You will need at the very least a user name.

If you have read access to IPC$ without auth, you can list domain users as `anonymous`

`python3 lookupsid.py anonymous@ip_address`

Usually you will need domain, username, password, target ip

`python3 lookupsid.py DOMAIN/user:password@ip_address`