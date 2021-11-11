## Types of Evasion

- On-Disk evasion
- In-Memory evasion

In-memory evasion is hindered by AMSI (Anti-Malware Scan Interface) which scans scripts as they enter memory.


---

## How AVs Detect

- Static Detection
- Dynamic / Heauristic / Behavioural Detection

Modern AV relies on a combo of these


**Static Detection**

Static detection involes some type of signature detection. Ex: taking the hashsum of a suspicious file and looking up in DB. 

*Byte/String Matching*
Another form of signature detection. Searches thru the program to match sequences of bytes against a known DB of bad byte sequences. This is much more effective than looking up hashsum


---

**Dynamic Detection**
Looks at how the file **acts** rather than how the file is built.
Checks against _pre-defined rules_

- AV can go thru executable line by line
- sandbox environments can be used to test suspicious files

Ex: ways to bypass sandbox. Check for fan, gui, resolution, vm tools. Program should exit if it detects it's in a VM.


[[random 1.png]]


