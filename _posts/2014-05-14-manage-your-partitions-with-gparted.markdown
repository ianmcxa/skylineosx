---
author: ian_mcxa
comments: true
date: 2014-05-14 02:43:11+00:00
layout: post
title: Manage your partitions with Gparted
wordpress_id: 605
categories:
- General
- Guides
tags:
- dual boot
- ext4
- GNU Parted
- Gparted
- hfs+
- ntfs
- partitioning
- vfat
---

One of the big issues facing dual, or triple boaters is partitioning the various filesystems and formats correctly. Windows, OS X and Linux all use different types of filesystems, and they aren't all compatible. To get around this issue you can use a bootable disk partitioning utility. Gparted is a linux based GUI tool that can help you partition your disks for any OS. One of the major advantages to this is that you can modify your partitions without completely wiping your drive and you can resize your partitions properly.


### Filesystem Types


Windows - exFAT (or NTFS on older versions)

Linux - ext3, ext4, btrfs and lots more.

OS X - hfs+ (this is the same as OS X Extended (Journaled))

OS X can see exFAT partitions but cannot modify them, and it cannot see ext3, ext4 or btrfs file systems.


### Installing Gparted


Gparted can be [installed to a USB](http://gparted.sourceforge.net/liveusb.php) or [burned to a CD](http://gparted.sourceforge.net/livecd.php). You can download the .iso file [here](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.18.0-2/gparted-live-0.18.0-2-amd64.iso/download).

It is much, much easier to install Gparted on a CD than on a USB and I recommend that you do this if you can. You can do this by right clicking on the .iso and clicking burn to disk.


#### USB installation instructions


To do this first you must insert a flash drive that you do not mind overwriting.

Then from the terminal issue the command _diskutil list_

The output should look similar to this.

![](http://cdn.osxdaily.com/wp-content/uploads/2009/10/list-mounted-drives.png)

From the output, you should be able to tell which disk is the the flash drive (hint: look at the size).

Once you are ABSOLUTELY CERTAIN that you know which device is the drive, you can issue the following command to overwrite it with the GParted iso.

_sudo dd if=_/path-to-gparted-live.iso _of=/dev/disk#__ bs=4M; sync_

Replace path-to-gparted with the actual path to the file. Usually this will be ~/Downloads/gparted-live-0.18.0-2-amd64.iso (bear in mind that the version may be different)

Replace /dev/disk# with the device node of your USB key. I.E /dev/disk2. Be absolutely sure that you enter the correct device node as an incorrect device node will overwrite your hard drive.


### Using GParted


At the Bios hold down the boot menu key, on my z77-ud5h this is the F12 key. From the boot menu select DVD drive/USB Media depending on where you installed Gparted and press enter. Gparted should now boot up.

![](http://distrowatch.com/images/cgfjoewdlbc/gparted.png)


The GParted Startup Screen




From here you will be able to add, delete, move, re-size and format partitions. Note: Always backup files before editing partitions as there is always a slight chance of data loss.




For more information on how to use GParted please visit [http://gparted.sourceforge.net/help.php](http://gparted.sourceforge.net/help.php)





### Sources


http://gparted.sourceforge.net/index.php
