Looking at `/login` we see 3 files

```
config.php
login.php
login.php.swp
```

`.swp` files are are created when there are unsaved changes in vi

we can download `login.php.swp` and run `strings`

```php
if (strcmp($password, $_POST['password']) == 0) {
if (strcmp($username , $_POST['username']) == 0) {
```

these two lines are important. we can see `strcmp` is being used to check user/pw. This is super insecure.

If `strcmp` is given an empty array to compare against a stored value, it will return NULL  

`==` only checks for equality, and in this situation, NULL = 0
(`===` checks for both value and type)

---
In Burp, we can change our request from this:
```
username=asdf&password=asdf2
```
to this
```
username[]=asdf&password[]=asdf2
```

This converts the variables to arrays and returns NULL value, bringing us to an upload page.

we can upload a php reverse shell. and access it in `/_uploaded`

This gives us our first shell