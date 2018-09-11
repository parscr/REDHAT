# Manage local linux users and groups

To create a local user: 
```
useradd parscr
```
passwd sets passwords:
```
passwd parscr
```
usermod modify existing users:
```
usermod --help
```
userdel username removes users but leaves the home directory
```
userdel parscr
```
userdel -r username removes the user and users home direcory
```
userdel -r parscr
```

groupadd creates group
```
groupadd groupname
```
groupadd -g to specify a specific GID
```
groupadd -g 50000 devops
```
groupmod 
```
groupmod -n devops test
```
groupmod -g 5000 devops
```
```
groupdel devops
```
```
usermod -g student student
```
```
usermod -aG groupname username
```
