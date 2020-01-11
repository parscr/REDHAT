Controlling services and daemons

Controlling the boot process

Runlevel | Target Units | Description
---------|--------------|------------
0        | runlevel0.target, poweroff target | shutdown and power off the system
1        | runlevel1.target, rescure target | setup a rescue shell 
2	 | runlevel2.target, multi user target | Set up a non-graphical multi-user system
3	 | runlevel3.target, multi user target | Set up a non-graphical multi-user system
4	 | runlevel4.target, multi user target | Set up a non-graphical multi-user system
5	 | runlevel5.target, graphical target  | Set up a graphical multi-user system
6	 | runlevel6.target, reboot target    | Shut down and reboot the system

setting a default target
```
systemctl get-default
systemctl set-default graphical.target
```

isolate, While the system is running, you can switch the target (run level), meaning only services as well as units 
under that target will now run on the system.

```
systemctl isolate graphical.target
```


Target | Purpose
-------|---------
graphical.target | System supports multiple users, graphics and text-based logins
multi-user.target | System supports multiple users text-based logins only
rescue.target | sulogin prompt, basic init completed
emergeny.targert | sulogin prompt, initramfs system root mounted on as read-only



Lab Controlling Services and daemons

1 Switch to the multi-user.target manually without rebooting
2 Configure your server to automatically boot into the multi-user.target after a reboot (reboot to verify)


```
systemctl get-default
systemctl isolate multiuser.target
systemctl get-default
```

```
systemctl set-default multiuser.target
systemctl reboot
```
