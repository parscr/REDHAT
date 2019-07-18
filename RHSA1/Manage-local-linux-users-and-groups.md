# Manage local linux users and groups

To create a local user: 
```
# useradd parscr
```
passwd sets passwords:
```
# passwd parscr
```
The default settings for new user can viewed and modified using the -D option
```
# useradd -D 
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
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
Granting Sudo Privileges to a User 
```
usermod -aG username wheel
```
List user in the wheel group
```
sudo lid -g wheel
```
