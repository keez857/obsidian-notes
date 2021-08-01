We are able to access ftp via anonymous login and we can grab `clean.sh`
from the scripts folder.

```bash
#!/bin/bash

tmp_files=0
echo $tmp_files
if [ $tmp_files=0 ]
then
        echo "Running cleanup script:  nothing to delete" >> /var/ftp/scripts/removed_files.log
else
    for LINE in $tmp_files; do
        rm -rf /tmp/$LINE && echo "$(date) | Removed file /tmp/$LINE" >> /var/ftp/scripts/removed_files.log;done
fi
```

1) we see that ftp is writable from the nmap scan
2) we see the script is deleting temp files, if there are no temp files it writes the line `Running cleanup script:  nothing to delete` > removed_files.log
3) we saw that it was actively writing new lines to removed_files.log because we downloaded it a second time and used `diff` and saw that there were more lines written. this means that there's cronjob running?
4) we then modify clean.sh with a bash reverse shell and upload it to the ftp /scripts directory with `put`


This grants us a shell with user `namelessone`