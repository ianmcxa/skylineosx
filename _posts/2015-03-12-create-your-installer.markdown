---
author: ian_mcxa
comments: true
date: 2013-12-30 08:22:24+00:00
slug: create-your-installer
title: Create Your Installer
permalink: /create-your-installer
---

You will need:



	
  * Flash Drive (at least 8GB)

	
  * A machine running OSX ([or a virtual machine](http://www.skylineosx.com/running-os-x-on-windows-virtualisation/))

	
  * [The Clover Installer](http://sourceforge.net/projects/cloverefiboot/)

	
  * [FakeSMC](http://www.osx86.net/files/file/3733-fakesmckext/) -absolutly necessary

	
  * [NullCPUPowermanagment](http://www.osx86.net/files/file/3465-nullcpupowermanagement-32-64-bit/) -useful if you have pm related kernel panics.

	
  * The 10.10 kernel which you can get the kernel [here](http://www.hackintoshosx.com/files/file/4169-mach-kernel-for-lapic-native-1010x/)


To get started go to the mac app store and download a copy of [OSX Yosemite](https://itunes.apple.com/WebObjects/MZStore.woa/wa/viewSoftware?id=915041082&mt=12) from the mac app store.


### **Format your USB Drive**


![Disk Utility](/images/installation/disk-utility.jpg)

Open disk utility, select your USB flash drive. Under the partition tab select 1 Partition. Set the format to Mac OS Extended (Journaled). Under the options menu, select GUID Partition table. Click Apply and wait.


### **Copying the Yosemite install files to your drive**


Navigate to the Install OS X Yosemite.app->(right click/show package contents)->contents->shared support and double click the InstallESD.dmg

Open the terminal and paste the following: _open /Volumes/OS X Install ESD/BaseSystem.dmg_

A BaseSystem drive should now appear on your desktop.

![Disk Utility RESTORE](/images/installation/disk-utility-restore.jpg)

Open Disk Utility and go to BaseSystem. Go to the restore tab and drag your flash drive to the destination and click apply. This will take some time.

You will now have 2 BaseSystem icons on your desktop. Look at the space available to determine which is your flash drive. I suggest you rename it for clarity.

Within your flash drive, navigate to /System/Installation and replace the packages alias with the packages folder found in the Install ESD drive.

Download the mach_kernel and copy it to the root of your flash drive. (You can also extract the kernel from OS X Install ESD/Packages/BaseSystemBinaries.pkg with [Pacifist](http://download.cnet.com/Pacifist/3000-2094_4-10135915.html))


### **Patch the Installer drive for PC**


Open the Clover Installer. Select your flash drive as the destination. Then click customize.

If you have a UEFI motherboard select the following:

![CloverSettings UEFI drive](/images/installation/cloversettings-uefi-drive1.jpg)

If you have a non-UEFI (bios mode) board select the following:

![CloverSettings non-Uefi drive](/images/installation/cloversettings-non-uefi-drive1.jpg)




#### Explanation of Installer Settings




##### Install for UEFI motherboards


Selecting this option will not install the traditional boot files. It will instead install Clover for use with UEFI booting.


##### Install boot0af in MBR


This option installs the Clover boot file. When the Clover boots, it will look in the boot0 sector of your drives for a boot file. If it finds one, it initiates the operating system.


##### CloverEFI 64-bits SATA


This gives Clover access to your hard drives through SATA, so it can initiate the operating system.


##### Theme


This will be what you see when clover loads. I use the bootcamp theme since it looks like the real OS X bootloader, but the choice is yours.

Note: Install only 1 theme from the installer.

[More info](http://clover-wiki.zetam.org/Design) on themes.


##### Drivers 32 and 64


These are extra drivers for Clover. They should not be essential.


##### Drivers64UEFI:


Because not all UEFI bios have all the correct drivers for Clover, you can install them here. The configuration shown is best for Gigabyte boards. For non Gigabyte boards install the displayed drivers with the addition of the OsxLowMemFixDrv-64.


#####  Install RC Scripts and Optional RC Scripts


These are scripts that help clover with shutting down and starting up. They are not needed on an installer drive, but are essential when installing to your startup drive.

Additional info available [here](http://clover-wiki.zetam.org/Installation#Using-the-installer).

Run the Installer. An EFI partition should now appear on your desktop.

Navigate to EFI->CLOVER->kexts->10.9 and copy FakeSMC.kext and NullCPUPowermanagment.kext


### **Copy over essential files**


Now on the root of your installer Create a folder named Files and copy:



	
  * The Clover Installer

	
  * FakeSMC.kext

	
  * NullCPUPowermanagment.kext

	
  * If you wish to use a post installation tool such as [Hackintosh Vietnam](http://www.osx86.net/files/file/3842-hackintosh-vietnam-ultimate-aio-tool/), download it and copy it to Files as well.


Next you will need to configure clover for your machine...
