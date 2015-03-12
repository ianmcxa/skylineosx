---
author: ian_mcxa
comments: true
date: 2014-01-11 00:09:57+00:00
slug: installing-osx
title: Installing OSX
permalink: /installing-osx
---

For this section you will need:



	
  * The Installation Flash Drive made in the previous guides.

	
  * A compatible machine with a Drive for use with OS X. (Note: It is possible to run OS X and windows on the same drive; however, I will not be covering that here)

	
  * Another computer or smartphone to get answers on if something goes wrong.

	
  * Time and patience.


To start, unplug all unnecessary devices from your computer. This includes all hard drives except the one you plan to install OS X on.


### **Initial Boot**


You should now be greeted by the clover boot screen. Use the left and right arrow keys to select your usb installer then press the spacebar. You should now see a menu. Navigate down, with the arrow keys, to _boot verbose mode_ and press enter.

The installer will take some time to load (can be up to 10 minutes depending on the speed of your flash drive). First you will see the Verbose output (white scrolling text on a black screen) and then a white screen as the installer loads.

_(No screenshots of this for now, as I have no idea how to get them)_

Note: If the installer hangs, the verbose output is very helpful for diagnosing the problem so take a picture of it or copy it down when asking for help.

Once the installer loads, click Continue and then agree to the terms and conditions. _Do not click install yet._

In the Menu bar select Utilities/Disk Utility. Disk utility should now open in a single window.

![Disk Utility INSTALATION](/images/installation/disk-utility-instalation.jpg)

Format the Hard Drive you want to install to with the same settings as the Flash Drive. 1 Partition, Name it 'Boot', Mac OS X Extended (Journaled), Guid Partition Table. Click Apply.

Now exit the close the disk utility menu, which should bring you back to the Installer.

Select 'Boot' as the destination, and click install. (this may take a while)

Upon finishing the install, your machine will automatically reboot.

When you reach the clover bootloader screen, Navigate over to Boot from 'Boot,' press space, navigate down to Verbose mode and press enter.

Note: Because the initial boot has to build the caches, it can take more time than a normal boot.

If all goes correctly, you will see the Setup Utility.

For now, select 'My computer does not connect to the internet' when prompted. Enter all other options normally. You should now be able to get to the desktop of your hackintosh.


### **Preparing**** for subsequent boots.**


Your hard drive still needs to be configured to boot on it's own without the help of a flash drive.

Open System Preferences->Privacy and Security. Set 'Allow Apps Downloaded From:' to Anywhere.

Now Navigate to your install Drive/Files and run the clover installer. This time select 'Boot' as the destination. Use the Same settings used for the flash drive, except this time be sure to install the RC scripts.

![Clover Settings Boot UEFI](/images/installation/clover-settings-boot-uefi.jpg)

_Settings for UEFI boards._

![Clover Settings non-UEFI Boot](/images/installation/clover-settings-non-uefi-boot.jpg)

_Settings for non-UEFI boards._

This should mount a separate EFI partition for your hard drive. (it should have a grey or yellow disk icon)

Open this partition and navigate to /EFI/CLOVER. Now, replace the config.plist with the one in 'Files' folder on your installer drive. Navigate to /EFI/CLOVER/kexts/10.10 and copy FakeSMC.kext from the 'Files' folder.

Power down your machine and remove your flash drive. WARNING: Do not attempt to remove the flash drive until your machine has completely powered down.

Boot to the bios.

Set your newly installed upon drive as the first boot option. If you are using UEFI, make sure you have selected the UEFI prefixed option. (I.E. _UEFI sandisk 120gb_ as opposed to _P0: sandisk 120GB_)

Save your configuration and reboot. Clover should boot you directly to your desktop, fancy apple logo and all.

Check out the [Post Installation](http://skylineosx.wordpress.com/post-installation/) for guides on enabling audio, internet and more.

NOTE: to install kexts simply copy them to /EFI/EFI/CLOVER/kexts/10.10 and reboot.
