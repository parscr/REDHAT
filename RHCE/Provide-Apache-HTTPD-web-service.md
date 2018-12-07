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
systemctl enable httpd
systemctl start httpd
systemctl reload httpd
systemctl restart httpd.service
systemctl status httpd
```
