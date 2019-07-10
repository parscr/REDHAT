# Provide Apache HTTPD web service

#### Install HTTPD
```
yum install httpd 
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

### Enable on boot start/reload/restart/status
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
sudo mkdir -p /var/www/html/download.example.ox.ac.uk/{public_html,logs}
```
```
vim /etc/httpd/conf.d/download.example.ox.ac.uk.conf
```
```
<VirtualHost *:80>
    ServerAdmin craig.parsons@example.ox.ac.uk
    ServerName download.example.ox.ac.uk
    ServerAlias www.download.example.ox.ac.uk
    DocumentRoot /var/www/html/download.example.ox.ac.uk/public_html/
    ErrorLog /var/www/html/download.example.ox.ac.uk/logs/error.log
    CustomLog /var/www/html/download.example.ox.ac.uk/logs/access.log combined
</VirtualHost>
```

### Check Syntax/Version

```
httpd -t
httpd -v
```
### Moving Virtual hosts location.
```
vim /etc/httpd/conf.d/download.example.ox.ac.uk.conf
```
```
<VirtualHost *:80>
    ServerAdmin craig.parsons@example.ox.ac.uk
    ServerName download.example.ox.ac.uk
    ServerAlias www.download.example.ox.ac.uk
    DocumentRoot /datapart1/www/html/download.example.ox.ac.uk/public_html/
    ErrorLog /datapart1/www/html/download.example.ox.ac.uk/logs/error.log
    CustomLog /datapart1/www/html/download.example.ox.ac.uk/logs/access.log combined
</VirtualHost>

<Directory /datapart1/www/html>
            Options Indexes FollowSymLinks
            Require all granted
            AllowOverrride None
</Directory>
```

