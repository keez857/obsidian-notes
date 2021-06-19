When looking at a giant config file with lots of options commented out, you can use grep to show only lines that begin without a comment symbol.
In this case, comments start with #

`grep -oE '^[^#].*' /path/to/file`