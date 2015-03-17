---
author: ian_mcxa
comments: true
date: 2014-06-07 03:45:10+00:00
layout: post
slug: yosemite-installation-guide
title: Yosemite Installation Guide
categories:
- bootloader
- Guides
- OS X
tags:
- '10.10'
- guide
- Hackintosh
- installation
- OS X
- Yosemite
---

OS X 10.10 DP1 has been out for a few days, so I thought I would compile an installation guide. Bear in mind that I haven't really had a chance to install the DP1, I generally like to wait for DP2 or 3 so that my OS isn't quite so buggy. DP1 is cool to experiment with, but I wouldn't want to run it as a daily driver just yet.

I'm going to assume that you have some experience with hackintosh installs, so I won't go into too much detail on the steps that have not changed. If this is your first hackintosh install, I suggest that you go with[ Mavericks ](/create-your-installer/)at least until the GM build of Yosemite. I will also assume that you are doing this on a mac or hackintosh.

Also let me give a huge shoutout to the guys at Insanelymac.com for the constant stream of awesome material and information following the Yosemite announcement, and a special thank you to the users snatch and ikingblack for the guides upon which this is based. I'd also like to thank Slice, the lead Clover dev, for his work adapting Clover for Yosemite so quickly.


### Requirements


For this guide you will need the .dmg file for OSX 10.10 DP1, you can get this from Apple's website if you are part of the paid Apple developer program. If you don't want to cough up the $100 to join, you can find the .dmg on various torrent websites.

You will also need [the latest build of Clover](http://sourceforge.net/projects/cloverefiboot/files/latest/download) Chameleon/Chimera is not going to work at this point.

The latest version of [FakeSMC.kext](http://sourceforge.net/projects/hwsensors/files/HWSensors.6.9.1315.Binaries.dmg/download)


### Creating the USB


For this guide I will be using a lot of terminal commands because they are easy to simply copy and paste.

As with previous versions, right click on the installer > show package contents

Navigate to Contents/Shared Support and double click on the InstallESD.dmg, the .dmg should now mount and appear on your desktop

In the terminal issue the following command:

`open "/Volumes/OS X Install ESD/BaseSystem.dmg"`

Now, in disk utility restore the BaseSystem.dmg to your usb stick. Now for the new stuff.

Rename your usb drive to Yosemite. (not the dmg) You can tell which drive is the USB from the size.

Issue the following commands:

`cp "/Volumes/OS X Install ESD/BaseSystem.dmg" /Volumes/Yosemite/`
`cp -a "/Volumes/OS X Install ESD/BaseSystem.chunklist" /Volumes/Yosemite/`
`rm /Volumes/Yosemite/System/Installation/Packages`
`cp -a /Volumes/OS X Install ESD/Packages /Volumes/Yosemite/System/Installation/Packages`

The last command may take some time to complete.

Now install Clover to your USB drive. The EFI partition of your usb drive should then appear. If you need help installing Clover, please read the Patch installer for PC section of  [the following guide](/create-your-installer/).

Run the following command:

`mkdir /EFI/Clover/kexts/10.10`
`open /EFI/Clover/kexts/10.10`

This will create and open the folder you need to copy your kexts into. Copy FakeSMC from the binaries folder you downloaded, also copy any other critical kexts that you need. I.E NullCPUPowerManagment.

You should also create a folder named Hackintosh on the root of your USB drive and copy FakeSMC, your network kexts and the Clover install dmg into that folder. It is critical to get the network kexts because we will use this folder later to copy kexts to our final installation.

Now open your Clover config file /EFI/Clover/config.plist This file can be opened in Xcode or Textwrangler and a few others but I do not believe it will work with text edit. Add the folowing lines to the end of the config file.

_ <key>Arguments</key>_
_ <string>kext-dev-mode=1</string>_

Save the file and exit.


### Installation and First Boot


At the clover boot prompt, press the spacebar and select 'With Injected Kexts'

The machine should now boot to the installer, though you may need to boot into safe mode (-x) for it to work properly.

Install OS X on the target drive.

Now reboot to clover, with the up and down arrows select your newly installed upon partition and press space. Then select 'With injected kexts' and enter your boot arguments as before.

Your system should now boot.


### Prepairing for subsequent boots


Install Clover on the hard disk, use the same settings as before. The EFI partition for the hard disk should mount.

Enter the following code in the terminal as before

`mkdir /EFI/Clover/kexts/10.10`
`open /EFI/Clover/kexts/10.10`

Then copy the kexts from the Hackintosh folder on the Yosemite drive to the 10.10 folder that you have just opened.

Lastly open the clover config file /EFI/Clover/config.plist and as before add these lines to the end.

_ <key>Arguments</key>_
_ <string>kext-dev-mode=1</string>_

You should now be able to boot directly from your Hard Drive.

Please do remember that DP1 is an early beta stage operating system that we just got access to. This means that not only will the OS have lots of bugs and glitches, but us hackintoshers have had very little time to experiment with the OS and to fix hackintosh related issues. Therefore, it may not even work on your machine yet, and if that is the case please do let us know.

If you just want to test out Yosemite on a USB, check out [WarDoctor's video tutorials](http://www.insanelymac.com/forum/topic/298438-1010-vanilla-bootable-usb-guide/).


### Sources


http://www.insanelymac.com/forum/topic/298521-easy-yosemite-1010-usb-installer/

http://www.insanelymac.com/forum/topic/298458-installation-guide-for-1010-dp1-usb/

http://www.insanelymac.com/forum/topic/298402-os-x-yosemite-dps-builds/
