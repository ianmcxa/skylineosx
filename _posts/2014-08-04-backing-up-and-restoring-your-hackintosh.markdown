---
author: ian_mcxa
comments: true
date: 2014-08-04 01:17:59+00:00
layout: post
slug: backing-up-and-restoring-your-hackintosh
title: Backing up and Restoring your Hackintosh
categories:
- General
- Guides
- OS X
---

![](/images/guide-images/osx-backup.jpeg)

Updating a hackintosh always has the potential for things to go wrong, so it is always recommended to have a backup copy of your data. The safest method is to have your data backed up to a seperate drive or NAS (Network Attached Storage); however, this can become very expensive especially if you have a lot of data. It can also be useful to backup your system to a seperate partition, so that you can revert if something goes wrong.


### Tools for creating Backups




#### ![Time Machine](https://upload.wikimedia.org/wikipedia/en/f/f1/Time_Machine.png) Time Machine - Graphical


Time machine is Apple's default backup mechanism. it works incredibly well alongside Migration Assistant to backup and restore data. If you want something that is very easy to use and well integrated, then time machine is your best option. Moreover, these is an application called [Time Machine Editor](http://timesoftware.free.fr/timemachineeditor/), which adds a lot of the functionality missing from Time Machine.


#### [SuperDuper - Graphical](http://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html)


SuperDuper is a 3rd party alternative to time machine. The basic version is free, but scheduled backups require the pro version which is priced at about $30. Unlike Time Machine, SuperDuper makes a full backup that is bootable. Note that booting from sepearate partitions on a single drive requires UEFI. If you make a copy of your drive using SuperDuper, you should see a second boot option in your Clover boot prompt saying something along the lines of "Boot OSX from Backup" or whatever you named your backup drive.


#### [Carbon Copy Cloner -Graphical](http://bombich.com/index.html)


Carbon Copy Cloner is very similar to SuperDuper. It schedules and creates fully bootable and restorable backups. You can also use these backups, as well as SuperDuper backups with Migration Assistant. Meaning that you can Create a backup > Clean install a new OS X version and then use Migration Assisstant to restore only your user files leaving the upgraded system untouched and fully functional. The only real downside to Carbon Copy Cloner is that it costs $40.


#### Rsync - Console


For more advanced purposes, or if you don't want to shell out the money for the previous two tools, you can always use the rsync command which is included with Mac OS X. Rsync will create full bootable volumes just as the graphical tools will. To create a backup with rsync follow these steps:

Note: Your account must be set to Administrator for this to work.



	
  1. Format your backup drive in Disk Utility to OS X Extended (journaled). We'll call it 'Backup' The drive should then mount and show up a drive on your desktop.

	
  2. Open a terminal and enter the following command: _sudo rsync -aAHXv /* /Volumes/Backup --exclude={".Spotlight-*/", ".Trashes", "/afs/*", "automount/*", "/cores/*", "/dev/*", "/Network/*", "/private/tmp/*", "/private/var/run*", "/private/var/spool/postfix/*", "/private/var/vm/*", "/Previous Systems.localized", "/tmp/*", "/Volumes/*", "/.Trash"}_

	
  3. If the system spits out an error saying one of the locations listed in the --exclude doesn't exist, you can remove it.

	
  4. You should now see a flood of filenames being listed as they are copied. This may take quite a bit of time.


Rsync supports incremental backups, so when you want to make your next backup simply run the command again with the _--delete_ option to remove files from the backup that you have deleted.


### Restoring to a newly upgraded system


Once you have upgraded or re-installed on your primary drive, you will want to restore all your data. The best way to do this is with Apple's Migration Assistant as it will restore all your files without messing up any system configuration. Simply Navigate to /Applications/Utilities and open it.

![](/images/guide-images/migrate.png)

Migration Assistant should then display any backup drives you have connected to your system directly or available over the network. Migration Assistant will work with any of the backup solutions listed above. It can also restore from another Hackintosh, Apple Mac or PC. Simply select the correct source and click continue.

Note: If you used the same username on both the new install and the system you are restoring from, Migration Assistant will ask if you wish to remove the account you created during the installation leaving your mac exactly as it was before.


### Restoring in the Event of System Failure


Here you have two options. You can perform a clean install and restore with Migration Assistant, or if you created a bootable backup you can start your system from the backup and restore to your primary drive. This can be done at the Clover boot prompt.

Once you have booted the backup drive, format your primary drive using disk utility, and then restore the drive through SuperDuper, Carbon Copy or with the following rsync command:

_sudo rsync -aAHXv /* /Volumes/<Name of the drive you are restoring to> --exclude={".Spotlight-*/", ".Trashes", "/afs/*", "automount/*", "/cores/*", "/dev/*", "/Network/*", "/private/tmp/*", "/private/var/run*", "/private/var/spool/postfix/*", "/private/var/vm/*", "/Previous Systems.localized", "/tmp/*", "/Volumes/*", "/.Trash"}_

You should then be able to reboot to your restored primary drive.


### Sources


http://mac.appstorm.net/roundups/utilities-roundups/8-backup-solutions-for-os-x/

http://timesoftware.free.fr/timemachineeditor/

http://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html

http://bombich.com/index.html

https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync

http://nicolasgallagher.com/mac-osx-bootable-backup-drive-with-rsync/
