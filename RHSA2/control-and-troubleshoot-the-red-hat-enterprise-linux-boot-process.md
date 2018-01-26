## Boot, reboot, and shutdown

```
systemctl poweroff
```
```
systemctl reboot
```

## Runlevel-Target
systemd uses ‘targets’ instead of runlevels. By default, there are two main targets:

multi-user.target: runlevel 3
graphical.target: runlevel 5

```
systemctl get-default
```
set a default target
```
systemctl set-default graphical.target
```
On a running system switch to a diffrent target
```
systemctl isolate multi-user.target
```

1. runlevel0.target -> poweroff.target
2. runlevel1.target -> rescue.target
3. runlevel2.target -> multi-user.target
4. runlevel3.target -> multi-user.target
5. runlevel4.target -> multi-user.target
6. runlevel5.target -> graphical.target
7. runlevel6.target -> reboot.target

## Reset the Root Password

* Reboot and enter the grub menu by pressing the **'e'** button 

* Find the linux16 or linuxefi line and add **rd.break selinix=0** to the end of the line

* start the boot process by pressing CTRL+x

###### remount the partition with Read/Wrire flags

```
#mount -o remount,rw /sysroot
#chroot /sysroot
```

###### Change the password

```
#passwd
```

###### SELinux relabel
```
#touch /.autorelabel
```

###### Exit from the shell and reboot

```
#reboot
```
