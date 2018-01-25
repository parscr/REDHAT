#Reset the Root Password

Enter Emergency mode

Reboot and enter grub edit menu by pressing the 'e' button 

Find the linux16 or linuxefi line and add rd.break selinix=0 to the end of the line

start the boot process by pressing CTRL+x

Reset the password

```
#mount -o remount,rw /sysroot
#chroot /sysroot
```

Change the password

```
#passwd
```

SELinux relabel
```
#touch /.autorelabel
```

Exit from the shell and reboot

```
#reboot
```
