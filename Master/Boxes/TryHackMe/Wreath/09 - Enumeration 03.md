Now that we know there is a dev copy of the website running on the personal PC.. 

We also know that uses the git server to control his projects. We can try to check the git repo and see if we can find any clues.

we can evil-winrm into the git server and find the git repo here:

`c:\gitstack\repositories\website.git`

We can navigate to the repositories  directory and use `Download website.git` to save the repo to our attack box

---

We have to use GitTools extractor so we can extract the contents of the git repo we stole.

`git clone https://github.com/internetwache/GitTools`

`./extractor.sh REPO_DIR DESTINATION_DIR`

This will created 3 directories, each of these respond to a commit

Each commit has a commit-meta.txt we can cat

We can use this bash liner to cat the commit-meta.txt files

`separator="======================================="; for i in $(ls); do printf "\n\n$separator\n\033[4;1m$i\033[0m\n$(cat $i/commit-meta.txt)\n"; done; printf "\n\n$separator\n\n\n"`

---

Based on the parents for each commit, the order

1.  70dde80cc19ec76704567996738894828f4ee895
2.  82dfc97bec0d7582d485d9031c09abcb5c6b18f2
3.  345ac8b236064b431fa43f53d91c98c4834ef8f3

Now we know that #3 is the latest build

---

We can search for php files to exploit

`find . -name "*.php"`

We find /resources/index.php

This is a file upload point. There is also basic auth on this page as noted in the comments

---

After analyzing the .php we can see that it uses a php technique that uses `getimagesize()` to check for exif data.

This helps to determine if the file uploaded is actually an 

---

Between lines 4 and 15:  
`$target = "uploads/".basename($_FILES["file"]["name"]);  
...  
move_uploaded_file($_FILES["file"]["tmp_name"], $target);  
`  

We can see that the file will get moved into an `uploads/` directory with it's original name, assuming it passed the two filters.