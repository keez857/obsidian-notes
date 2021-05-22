There are two primary types of evasion
- On-Disk evasion
- In-Memory evasion

In-memory evasion is hindered by AMSI (Anti-Malware Scan Interface) which scans scripts as they enter memory.


---

There are generally two categories for detection
- Static Detection
- Dynamic / Heauristic / Behavioural Detection

Modern AV relies on a combo of these

---

**Static Detection**

Static detection involes some type of signature detection. Ex: taking the hashsum of a suspicious file and looking up in DB. 

Byte/String Matching
Another form of signature detection. Searches thru the program to match sequences of bytes against a known DB of bad byte sequences. This is much more effective than looking up hashsum


---

**Dynamic Detection**


