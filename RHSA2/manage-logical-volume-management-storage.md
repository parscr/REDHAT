 ## Manage logical volume management (LVM) storage.

Adding a disk LVM

To show the available disks.

 ```
#fdisk -l
 ```
We assume our new disk is /dev/sdc and we will not create a partition on it but use /dev/sdc as it is. 
This gives us the advantage that if we increase the disksize outside of the OS

 ```
#pvcreate /dev/sdc
 ```
You can check what you have created by using

```
#pvdisplay
#pvdisplay -v
```
If you make a mistake you can remove with

```
#pvremove /dev/sdc
```

If you get the error below when doing a pvcreate.

```
#pvcreate /dev/sdc
Device /dev/sdb excluded by a filter.
```

If you are using a whole disk device for your physical volume, the disk must have no partition table. For DOS disk partitions, the partition id should be set to 0x8e using the fdisk or cfdisk command or an equivalent. For whole disk devices only the partition table must be erased, which will effectively destroy all data on that disk. You can remove an existing partition table by zeroing the first sector with the following command:

```
#dd if=/dev/zero of=/dev/sdc bs=512 count=1
```


Now we create a volume group called vg_datapart1

```
#vgcreate vg_datapart1 /dev/sdc
```

You can check what you have created by using

```
#vgdisplay
```

Now we create a volume called lv_datapart1 and give it all available free space on the vg_datapart1

```
#lvcreate -l+100%FREE -n lv_datapart1 vg_datapart1
```

You can check what you have created by using

```
#lvscan
#lvdisplay
```

Alternative to create only 20GB use:

```
#lvcreate --size 20G -n lv_datapart1 vg_datapart1
```

Create a filesystem on top of the lv_data

```
#mkfs -t xfs /dev/vg_datapart1/lv_datapart1
```

Create the mount point

```
#mkdir /datapart1
```

Get UUID for /etc/fstab

```
#blkid
```

example output

```
/dev/block/8:2: UUID="iS1aIl-cvGX-MaAm-WrRJ-9m5U-AWvk-F0YZ1c" TYPE="LVM2_member"
/dev/block/253:1: UUID="6085f9f1-e5c7-4030-8472-0cd7aeb22998" TYPE="xfs"
/dev/block/8:1: UUID="32d7dd18-3c7f-4ddd-a7f0-5fd6b575a51c" TYPE="xfs"
/dev/block/253:0: UUID="808996b2-33dd-44c3-abe3-95ebd977cf90" TYPE="swap"
/dev/dm-1: UUID="6085f9f1-e5c7-4030-8472-0cd7aeb22998" TYPE="xfs"
/dev/sda1: UUID="32d7dd18-3c7f-4ddd-a7f0-5fd6b575a51c" TYPE="xfs"
/dev/dm-0: UUID="808996b2-33dd-44c3-abe3-95ebd977cf90" TYPE="swap"
/dev/sdc: UUID="qGtaOX-s3Z3-VS0d-5iuu-eA9f-mul7-nDsoaD" TYPE="LVM2_member"
/dev/sdb1: LABEL="DATAPART1" UUID="AED61027D60FEE81" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="d3f886a4-4282-4dbb-b6f8-cd7bf6549600"
/dev/mapper/vg_datapart1-lv_datapart1: UUID="3e7d0b26-e993-4a96-a653-462337863252" TYPE="xfs"
/dev/mapper/centos-home: UUID="99841ecc-1d6c-4ce0-86e4-79c9e1555e3f" TYPE="xfs"
```

```
#vi /etc/fstab
```
insert example

    UUID="3e7d0b26-e993-4a96-a653-462337863252" /datapart1 xfs defaults     0 0

Mount using the command

```
#mount /datapart1
```
