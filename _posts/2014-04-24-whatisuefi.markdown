---
author: ian_mcxa
comments: true
date: 2014-04-24 22:24:37+00:00
layout: post
title: What is UEFI and how it is useful for Hackintoshing.
categories:
- General
- OS X
tags:
- BIOS
- boot
- bootloader
- chameleon
- Clover
- CSM
- dual boot
- EFI
- UEFI
- United Extensible Firmware
---

There are two basic methods of installing a bootloader: BIOS and UEFI. This article will explain them both, as well as what they mean for in terms of hackintoshing.


### What is/are BIOS?


BIOS was the original firmware standard used on IBM PC's and then by all the IBM clones. As such, it became the standard used by DOS and then Windows. It can be accessed by holding down a function key at boot, and can edit basic hardware settings.



![BiosBoot](/images/guide-images/BiosBoot-300x300.jpeg)


The BIOS Boot Process




The BIOS selects the drive to boot from and triggers the code in the MBR or Master Boot Record. This is the very first thing on the drive. The MBR then loads the bootloader which allows you to select a partition and trigger the kernel on that partition. The kernel then loads the rest of the operating system.




The important thing of note here is that the BIOS can only see physical drives, not partitions.




What this ends up meaning is that BIOS is a very simple. You install a bootloader to the MBR and that bootloader gets triggered. It is very good for dual booting between separate drives, as you can keep the bootloaders on each drive completely separate and distinct regardless of whatever partitioning you may have done.





### What is UEFI?


UEFI (United Extensible Firmware Interface) a firmware standard designed to replace BIOS (Basic Input Output System). UEFI is included on nearly all modern motherboards, and can be useful for hackintoshes.

![UEFIBoot](/images/guide-images/UEFIBoot.jpeg)




The UEFI Boot Process




UEFI is far more complicated. There is a ton going on under the hood that I don't have the knowledge to properly explain. In practice, UEFI can decrease boot times and see separate partitions on a drive. It also uses a partition called the EFI partition, which is used to store the bootloader.




This means that you can install OS X and Windows (7 or 8) on separate partitions of the same drive, install Clover as the EFI bootloader and select what OS to boot into just like on Apple's Bootcamp.




You can also use the EFI partition to make a more vanilla installation by keeping all your kexts and bootloader config files in the EFI partition. This allows you to use App Store updates without the fear of bricking your hack. However, since all OS X drives have a hidden EFI partition to start with, you can also do this through BIOS booting.




UEFI also provides the EFI shell which allows you to do more advanced debugging and configuration directly from the UEFI.




The downside to all of this is that UEFI is a bit trickier to get working, and you can only use an EFI bootloader like Clover, which is not everyone's first choice.





#### CSM (compatibility support module)


CSM is the backwards compatibility mode for UEFI motherboards. If you have a UEFI motherboard and boot using the regular BIOS method, then you are using CSM. The term UEFI Bios is incorrect as UEFI and BIOS are completely different things.


### UEFI vs BIOS


UEFI Advantages



	
  * Faster boot times

	
  * Can see partitions

	
  * Bootloader in separate partition

	
  * UEFI Shell


BIOS Advantages

	
  * Simple for dual booting on separate drives.

	
  * Can use Chameleon

	
  * Easier to get working


Generally UEFI is a better option; however, BIOS or CSM is a bit simpler to setup.

For more information on UEFI go to [www.uefi.org](http://www.uefi.org/)


### Sources


https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface

https://en.wikipedia.org/wiki/BIOS

http://www.uefi.org/faq
