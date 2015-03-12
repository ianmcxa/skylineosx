---
author: ian_mcxa
comments: true
date: 2014-01-10 23:03:00+00:00
slug: bios-configuration
title: BIOS Configuration
permalink: /bios-configuration
---

For this section you will need:



	
  * The machine you plan to install on.

	
  * The installer created in steps 1 and 2.

	
  * Your motherboard's manual and/or a smartphone to look up the bios options.


Plug your flash drive into your machine and boot to the BIOS. (for my board I press the delete key)

You will now need to configure the BIOS for use with Clover. Each board will be different, so I suggest looking up each setting in your motherboard manual to find out where it is. Some boards, particularly those without UEFI will not have many of the advanced settings. In this case, simply skip the step and continue.


### **Bios Features**


![BIOS features](/images/installation/bios-features.jpg)

_BIOS screenshots taken from the Gigabyte z77x-ud5h_

Select your install drive as the first boot option. If you are installing Clover on a UEFI board, there will be two boot options for your usb. Select the one prefixed with UEFI. (I.E _UEFI usb flash drive_)

CSM must be disabled. [this setting will not exist on non-UEFI installs] Note: this is required for most systems to boot. However, on my system (z77x-ud5h and Evga GTX 660) disabling CSM prevented the graphics card from functioning. I suggest that you try to boot with CSM disabled and if this causes issues with your card ( I.E. Your BIOS won't even be displayed.), then clear the CMOS and proceed with CSM enabled.


### **Peripherals**


![Peripherals BIOS](/images/installation/peripherals-bios.jpg)

SATA mode Selection must be set to AHCI

xHCI must be set to AUTO [this setting may not exist for all boards]

XHCI hands-off and EHCI hands-off much both be enabled. [this setting may not exist for all boards]


### **Power ****Management**


![Power Managment BIOS](/images/installation/power-managment-bios.jpg)

Wake on LAN must be disabled.

Soft-Off by PWR-BTTN set to delay 4 seconds (this is not essential, but it may fix shutoff/reboot issues)

Now save your BIOS configuration and reboot to begin the installation...
