---
author: ian_mcxa
comments: true
date: 2014-05-11 01:33:28+00:00
layout: post
slug: how-to-fix-imessage-issues-and-why-they-occur-in-the-first-place
title: How to fix iMessage issues, and why they occur in the first place
wordpress_id: 699
categories:
- General
post_format:
- Image
---

One very common issue with Hackintoshes is an inability to log in to iMessage, iCloud, ect. There have been various fixes for the issue; however, they are somewhat scattered throughout forum sites; I will attempt to assemble them here.


### Why the issue occurs


There are two basic reasons:

Apple computers store a lot of their identification information in their BIOS. This causes a lot of issues for hackintoshes because OS X assumes that information will be there, and it cannot boot without it. We get around this issue by injecting SMBIOS through our bootloaders. This way OS X believes it's running on a real mac and can access all the identification stuff it needs to run. However, Apple's services attempt to read the serial number of the motherboard, which they cannot do on a hackintosh. This causes them to fail.

The second issue is a result of OS X's naming convention for network interfaces. Hackintoshes use a much wider verity of wireless cards, so they may end up with an identifier that OS X and Apple's services may not be designed to handle.


### How to fix the issue with Clover


The latest versions of clover automatically inject the motherboard serial number, so that is not an issue. Just make sure you are running the latest build of Clover.

The second issue can be solved with automatic DSDT patches which can be activated from the [Clover Configurator](http://www.osx86.net/files/file/49-clover-configurator/).

Launch the Clover Configurator and open your config file /EFI/CLOVER/config.plist

_For a wired connection_: Under the ACPI tab, check the **FixLan** patch under the Old Way DSDT Patches.

_For a wi-fi: _Check the Wifi or **FixAirport** option.

Save your config file and restart your machine

You will then need to delete and re add your connection under System Preferences>Networking be sure to name it **en0**


### How to fix the issue with Chameleon/Chimera


Chameleon makes this fix a good bit more complicated, and as far as I can tell it only works with wired connections.

First we must install the NVRAM module. Download the file from [here](http://public.xzenue.com/downloads/download.php?fname=./FileNVRAM/FileNVRAM-1.1.3.zip). Credits to xZeneu

Now unzip the archive, and move the FileNVRAM.dylib to /Extra/modules/ If there is no module folder in /Extra, create one.

This should solve the serial numeber issue. Now for the network interface.

If you do not have it already, download the [Chameleon Wizard](http://dl.dropbox.com/u/7085278/Chameleon_Installer/download.html). Credit to janek202 of Insanelymac.

Open up Chameleon Wizard and navigate to the org.chameleon.boot tab.

Under Miscellaneous, check **Ethernet Built-In** and click save.

Reboot your machine.

Now, under System Preferences>Networking remove your current connection and add it back with the name **en0**.

### Update

This no longer works on OSX Yosemite.

### Sources


http://clover-wiki.zetam.org/Fixing-DSDT

http://www.osx86.net/topic/16080-guide-imessage-fix-with-chameleon/

http://www.insanelymac.com/forum/topic/286563-filenvram-113-released/

http://www.insanelymac.com/forum/topic/257464-chameleon-wizard-utility-for-chameleon/




https://www.youtube.com/watch?v=h1UObjrlpl0#t=47

