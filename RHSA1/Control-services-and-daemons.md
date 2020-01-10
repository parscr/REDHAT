Controlling services and daemons

service | systemctl | Description
--------|----------|------------------
service name start | systemctl start service.name | starts a service
service name stop | systemctl stop service.name | stop a service
service name restart | systemctl restart service.name | restart a service
service name reload | systemctl reload service.name | reload a service
service name status | systemctl status service.name | check if a service is ruinning
service name status | systemclt is-active service.name | check is a service is running

example enable, start and check the status of a service.
```
systemctl enable httpd.service
systemctl start httpd.serivce
systemctl status httpd.service
systemctl is-active httpd.service
```


chkconfig | systemctl | Description 
----------|-----------|-------------
chkconfifg name on | systemctl enable service.name| enable a service
chkconfig name off | systemctl disable service.name | disable a service
chkconfig --list name | systemctl is-enabled service.name | check if a service is enabled
chkconfig --list | systemctl list-unit-files --type service | list all services and check if they are enabled

masking and unmask a service 
```
systemctl mask iptables 
systemctl umask iptables
```

State of service.

keyword | Description 
--------|------------
loaded | unit configuration has been processed 
active (running) | running with one or more continuing processes
active (exited) | succesfully completed a one-time configuration
active (waiting) | running but waiting for an event
inactivce | not running
enabled | will be started at boot time
disabled | will not be started at boot time
static | can not be enabled but may be started by an enabled unit automatically


LAB Controlling services and daemons.

1. Start the psacct  service
2. Configure the psacct service so that it starts at system boot
3. Stop the rsyslog service 
4. Configire ryslog service so that it does not start at systrem boot

```
systemctl start psacct
systemctl status psacct
```
```
systemctl enable psacct
systemctl status psacct
```
```
systemclt stop rsyslog
systemctl is-active rsyslog
```
```
systemctl disable rsyslog
systemctl is-active rsyslog
```




