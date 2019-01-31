### Limit network communication with firewalld.

## Install firewalld
```
yum install firewalld
```
## start and enable firewalld
```
systemctl enable firewalld.service
systemctl start firewalld.service
```
##  Mask the iptables service which will prevent iptables from being started by another services:
```
systemctl mask iptables
systemctl mask ip6tables
```
## check current firewall state rules
```
firewall-cmd --state
firewall-cmd --get-default-zone
firewall-cmd --list-all
firewall-cmd --get-active-zones
```
## add a service
```
firewall-cmd --zone=public --add-service=http
firewall-cmd --zone=public --list-services
firewall-cmd --zone=public --permanent --add-service=http
firewall-cmd --zone=public --permanent --list-services
```
## add a port
```
firewall-cmd --zone=public --add-port=6007/tcp
firewall-cmd --zone=public --add-port=6007/udp
firewall-cmd --zone=public --list-ports
```
## permanent firewall
```
firewall-cmd --zone=public --permanent --add-port=6007/tcp
firewall-cmd --zone=public --permanent --add-port=6007/udp
firewall-cmd --zone=public --permanent --list-ports
```
## reload firewall
```
firewall-cmd --reload
```
## stop and disable firewalld in next boot
```
systemctl stop firewalld
systemctl disable firewalld
```
