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
firewall-cmd --list-all  
```

Configuring a Samba Server
The default configuration file /etc/samba/smb.conf

Samba uses /etc/samba/smb.conf as its configuration file.
If you change this configuration file, the changes do not take effect until you restart the Samba daemon
with the following command, as root:

```
systemctl restart smb.service
```

Prepare shared directories

/srv/ansys_docs		a read-only-share  
/srv/scratch		a read-write-share all-users  
/srv/samba_group 	a group share  

```
mkdir /srv/{ansys_docs,scratch,devops_group}
```

Make backup of smb.conf

``` 
cp /etc/samba/smb.conf /etc/samba/smb.conf.`date -I`
```

Configure the samba server

```
vi /etc/samba/smb.conf
```

```
[global]
	workgroup = RHCE
	security = user
	guest account = nobody
	map to guest = Bad user
	server string = engs-glyme Samba server sharing samba_pub and samba_group
 	netbios name = engs-glyme

	passdb backend = tdbsam

	printing = cups
	printcap name = cups
	load printers = yes
	cups options = raw

```
read-only share 

```
[ANSYS_DOCS]
	comment = ANSYS_DOCS Read-Only-Samba-Share
	path = /srv/ansys_docs
	readonly = yes
	guest ok = yes
```


read-write share all users

```
mkdir /srv/scratch  
chmod -R 0755 /srv/scratch/  
chown -R nobody: /srv/scratch/  
```

```
[SCRATCH]
        comment = SCRATCH_SPACE all-users-read-write
        path = /srv/scratch
        browsable = yes
        guest ok = yes
        read only = no
```

group share read-write-for-devops-group   
We want to give read-only privileges for all users who are not members of the devops group    

```
[DEVOPS]
	comment = devops group share
	path = /srv/devops_group
``` 
