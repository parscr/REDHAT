Control services and daemons

service | systemctl | Description
--------|----------|------------------
service name start | systemctl start service.name | starts a service
service name stop | systemctl stop service.name | stop and service
service name restart | systemctl restart service.name | restart a service
service name reload | systemctl reload service.name | reload a service
service name status | systemctl status service.name | check if a service is ruinning


chkconfig | systemctl | Description 
----------|-----------|-------------
chkconfifg name on | systemctl enable service.name| enable a service
chkconfig name off | systemctl disable service.name | disable a service
chkconfig --list name | systemctl is-enabled service.name | check if a service is enabled
