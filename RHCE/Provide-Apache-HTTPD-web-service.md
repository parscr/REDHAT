# Provide Apache HTTPD web service

#### Install HTTPD
```
yum install httpd
yum install  
```
```
yum group list
yum group info "Basic Web Server"
yum group install "Basic Web Server"
```
```
yum group list
yum group info "Web Server"
yum group install "Web Server"
```

### enable stop/start/restart
```
systemctl enable httpd.sevice
systemctl start httpd.service
systemctl reload httpd.service
systemctl restart httpd.service
systemctl status httpd.service
```
## Configure Firewalld.
```
firewall-cmd --zone=public --permanent --add-service=http
firewall-cmd --zone=public --permanent --add-service=https
firewall-cmd --reload
```
