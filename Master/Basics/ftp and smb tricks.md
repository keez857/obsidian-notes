### ftp
prompt off
mget *

### smb
recurse on
prompt off
mget *

These will grab all files you have permission to

---


wget -r ftp://anonymous:anonymous@10.10.160.40:7231