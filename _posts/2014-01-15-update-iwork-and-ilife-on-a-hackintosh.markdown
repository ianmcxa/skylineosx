---
author: ian_mcxa
comments: true
date: 2014-01-15 22:24:58+00:00
layout: post
slug: update-iwork-and-ilife-on-a-hackintosh
title: Update iWork and iLife on a Hackintosh
categories:
- General
tags:
- '10.9'
- Apple
- Clover
- Fix
- Hackintosh
- iLife
- iWork
- Mac
- Mavericks
- Update
---

OS X 10.9 introduced updated versions of iWork, iLife and Aperture. They offered the software free to new mac owners and users who owned previous versions of the software; this included the trial versions of iLife, iWork and Aperture. However, attempting to update them from a Hackintosh running Chimera or Chameleon (Clover does not have this issue) resulted in a message saying that the Apps were signed by a different AppleID, even if you had legitimately purchased them.

The simplest solution is to create a drive with the Clover bootloader, update the apps and boot back to your regular bootloader. Of course [switching to Clover](http://www.skylineosx.com/installation/switching-from-chameleonchimera-to-clover/) would fix the issue too.


### Creating the Boot Drive


For this you need a flash drive. It can be really any size since the only thing we need to put on it is Clover.

Download [Clover](http://sourceforge.net/projects/cloverefiboot/files/latest/download) and the [Clover Configurator](http://www.osx86.net/files/download/49-clover-configuratorconverter/)

![Disk Utility](/images/guide-images/disk-utility.jpg)

Format your Drive as Mac OS X Extended (Journaled), with Guid Partition Table.

![CloverSettings non-Uefi drive](/images/guide-images/cloversettings-non-uefi-drive1.jpg)

Now run the Clover installer to your drive, with the following settings.

Remember to include the OsxLowMemFix if you do not have a Gigabyte motherboard.

An EFI partition should now mount on your desktop.


### Configuring The Boot Drive


Install the Clove Configurator.

Launch it load your config.plist File->Open->/EFI/CLOVER/config.plist

If you boot with ncpi=0x200 or 0x3000 make sure that these options are checked under Boot.

If you have integrated graphics make sure that under Graphics, 'Inject Intel' is checked.

Under System Parameters check 'Inject System ID'

Now Save the config File and Exit.

Note: If you use a DSDT, copy it to /EFI/CLOVER/ACPI/patched


### Booting from the Drive


At startup, enter your boot menu (for me this is done by pressing F12) Select your USB device.

When you reach the Clover screen, use the arrow keys to select your Boot drive and press enter.

You're machine should now boot. Note, that the boot time may be significantly longer due to the speed of the flash drive.


### App Store Download


You should now be able to go to the App Store and upgrade your iWork and iLife Apps. You can simply begin the download, pause it and resume when booted back from your hard drive. The Apps should now show up under the purchased tab on the App Store, so you can install them to any other hackintosh even if it is running Chameneon/Chimera.


### A Note About Legality


There has been some controversy over whether it is piracy to upgrade the trial versions of apps to the new full fledged ones as the App Store will allow you to do. In terms of the law, it is completely fine. The trial software was, and still is, available from Apple's website and updating via the App Store breaks no violates no terms.

As far as ethics, it is up to you. Apple knows full well that this is possible and has taken no steps to prevent it.


### Sources:


http://www.tuaw.com/2013/10/24/illegal-trial-and-disc-versions-of-iwork-and-ilife-are-updatin/

http://www.mactrast.com/2013/10/truth-free-mac-app-store-software-upgrades-os-x-mavericks/
