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

### enable on boot stop/start/restart
```
systemctl enable httpd.sevice
systemctl start httpd.service
systemctl reload httpd.service
systemctl restart httpd.service
systemctl status httpd.service
```
### Configure Firewalld.
```
firewall-cmd --zone=public --permanent --add-service=http
firewall-cmd --zone=public --permanent --add-service=https
firewall-cmd --reload
```
### Virtual host
```
sudo mkdir -p /var/www/html/download.eng.ox.ac.uk/{public_html,logs}
```
```
vim /etc/httpd/conf.d/download.eng.ox.ac.uk.conf
```
```
<VirtualHost *:80>
    ServerAdmin craig.parsons@eng.ox.ac.uk
    ServerName download.eng.ox.ac.uk
    ServerAlias www.download.eng.ox.ac.uk
    DocumentRoot /var/www/html/download.eng.ox.ac.uk/public_html/
    ErrorLog /var/www/html/download.eng.ox.ac.uk/logs/error.log
    CustomLog /var/www/html/download.eng.ox.ac.uk/logs/access.log combined
</VirtualHost>
```

### Check Syntax/Version

```
httpd -t
httpd -v
```


