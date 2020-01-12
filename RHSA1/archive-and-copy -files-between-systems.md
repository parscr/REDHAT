# Archiving and copying files between systems.

Command | Description 
--------|------------
tar cvf |Archive files and directories with tar
tar tvf |List contents of a tar archive
tar xvf |Extract tar archive

```
tar cvf archivename.tar /files-you-want-to-backup
tar tvf archivname.tar
tar xvf archivename.tar
```
extract files to a target direcory
```
tar -xvf archivename.tar -C /tmp
```

Using Compression

command | Description
--------|------------
tar czf |Create gzip compressed tar archive
tar cjf |Create bzip2 compressed tar archive
tar cJf |Create xz compressed tar archive
tar xzf |Extract gzip compressed tar archive
tar xjf |Extract bz2 compressed tar archve
tar xJf |Extract xz compresssed tar archive

Append Update the archive

```
tar rfv archivename.tar /etc/hosts
tar uvf archivename.tar /files-you-want-to-update
```

lab

1. Archive the contents of the /etc directory
2. Extract the password files to the /tmp directory
3. Create a compressed archive of your /home directory
4. Create one archive file that contains the contents of /home and /etc
