## ftp

We are allowed anon ftp access.

After logging in there is a `note.txt`

Looking at the note we get creds

```
10201321:cd73502828457d15655bbd7a63fb0bc8
```


---

## http

we see there is an `http://academy.tcm/academy` page

I could not log in with the creds above.

I used SQLi on the username/password field with this payload:

```
' or 1=1 -- -
```

Login was successful as Rum Ham

There is a photo upload portion that could be useful. After uploading an image, we see it is stored in this directory:

```
http://academy.tcm/academy/studentphoto/
```

I uploaded a reverse php shell, set up my netcat listener, then refreshed the page.

I was able to get a shell as www-data


---

###