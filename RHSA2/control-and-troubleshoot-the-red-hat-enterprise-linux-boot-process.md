# Reset the Root Password

* Reboot and enter the grub menu by pressing the **'e'** button 

* Find the linux16 or linuxefi line and add **rd.break selinix=0** to the end of the line

* start the boot process by pressing CTRL+x

### remount the partition with Read/Wrire flags

```
#mount -o remount,rw /sysroot
#chroot /sysroot
```

### Change the password

```
#passwd
```

### SELinux relabel
```
#touch /.autorelabel
```

### Exit from the shell and reboot

```
#reboot
```
