Works by dumping the TGT from the LSASS memory of the machine

Local Security Authority Subsystem Service (LSASS) is a memory process that stores credentials on AD server

LSASS can store kerberos ticket along with other creds to act as gatekeeper.

Dumping tickets with mimikatz will give you a `.kirbi` file.

---

