---
layout: post
title: Create a new LVM partition
categories: filesystem
permalink: /:categories/:title
---

### Create a LVM VG, if you do not have an existing one:

For example: `fdisk /dev/hdb`

### Create an LVM physical volume (PV) using the pvcreate command
For example: `pvcreate /dev/hdb1`

### Create an LVM VG.
For example, to create a VG called VolGroup00 under /dev, run:

`vgcreate VolGroup00 /dev/hdb1`

### Create a LVM LV on the VG.
For example, to create an LV called kvmVM under the /dev/VolGroup00 VG, using 100% disk run:

`lvcreate -l 100%FREE -n kvmVM VolGroup0`


### Create a new filesystem. We are using EXT4 as an example.

`mkfs.ext4 /dev/VolGroup0/kvmVM`

