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
6	 | runlevel6.target, reboot targetr    | Shut down and reboot the system
