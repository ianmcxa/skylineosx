---
author: ian_mcxa
comments: true
date: 2014-01-17 22:29:25+00:00
slug: enable-speedstep
title: Sleep and Speedstep
permalink: /patch-sleep
---

To get sleep working in Clover is fairly straightforward. It should function normally once speedstep is enabled. However, not all devices will wake the machine (I.E. mouse and keyboard). Single pressing your power button should wake the machine if these do not.


### What is Speedstep?


Intel Speedstep is a power management function which allows your CPU to slow down when it is not under heavy use. This saves power and lengthens the life of your CPU.

To get this working in Clover we will need few things set up.



	
  * A DSDT must be present in /EFI/CLOVER/ACPI/patched

	
  * P and C state generation needs to be enabled. (this generates the SSDT tables needed for power management)

	
  * The HPET patch needs to be applied in the Clover Configurator




### Extract Your DSDT


Download the DSDT extraction script from [RampageDev](https://dl.dropboxusercontent.com/u/88732606/Guides/DSDTExtract%20.command.zip)

Double click the script to run it.

You should now see a DSDT.aml file on your desktop.

Copy it to /EFI/CLOVER/ACPI/patched


### Enabling Speedstep in the Clover Configurator


Launch the Clover Configurator.

Load your config file File->Open->/EFI/EFI/CLOVER/config.plist

![fix speedstep](/images/guide-images/acpi-sleep.png)

Make Sure P and C state generation is enabled.

Enter the name of your DSDT under the DSDT name (note: the name should be DSDT.aml and it is case sensitive)

Save the file and exit.

Reboot to apply changes.


### Common Fixes


If sleep does not function, try the following.



	
  1. Make sure you do not have NullCPUPowerManagment.kext installed in either /System/Library/Extensions or /EFI/CLOVER/kexts/10.9

	
  2. Enable the AppleRTC patch in the Clover Configurator.

	
  3. If you are using UEFI try removing the CsmVideoDxe driver from /EFI/CLOVER/drivers64UEFI (You may not have this installed, so if it isn't there don't worry.)


If sleep still does not function, ask for help in the comments or on one of the [hackintosh forum sites](http://www.skylineosx.com/additional-resources/).


### Sources


http://clover-wiki.zetam.org/Native-speedstep

http://clover-wiki.zetam.org/Sleep-problems

https://rampagedev.wordpress.com/guides/extract-your-own-dsdt/

http://www.projectosx.com/forum/index.php?showtopic=2562
