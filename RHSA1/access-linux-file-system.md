Accessing Linux File System

Searching with find 

option | command | Description
-------|---------|-------------
-name | find / -name hosts| to search for a file named hosts in the / directory and subdirectories
-iname| find / -iname *messages | case insensitive search will find upper and lowercase
-user | find / -user john | find all users owned by user john
-size +N/-N | find / -size +5M | find files more then 5M in size 
-exec | find / -exec | blurb

