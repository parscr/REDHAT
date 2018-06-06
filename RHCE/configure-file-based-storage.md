Provide file-based storage
NFS exports and SMB files shares.

# SAMBA

Install the samba package

```
yum install samba
```

Samba Daemons and Services

smbd  
nmb  
winbind  

```
systemctl enable smb nmb
```

Allow samba serice.

```
firewall-cmd --permanent --add-service=samba
firewall-cmd --reload
```

Configuring a Samba Server
The default configuration file /etc/samba/smb.conf

Command-Line Configuration
Samba uses /etc/samba/smb.conf as its configuration file.
If you change this configuration file, the changes do not take effect until you restart the Samba daemon
with the following command, as root:

```
systemctl restart smb.service
```
