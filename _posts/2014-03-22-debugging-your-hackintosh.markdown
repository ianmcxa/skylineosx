---
author: ian_mcxa
comments: true
date: 2014-03-22 05:47:44+00:00
layout: post
slug: debugging-your-hackintosh
title: Debugging Your Hackintosh
categories:
- Fixes
- General
- Guides
- Hardware
- OS X
tags:
- -v
- -x
- Boot Flags
- bootloader
- graphics enabler
- kernel panic
- safe mode
- troubleshooting
- verbose
---

The downside of having a Hackintosh is that when things go horribly wrong, you must fix it yourself. In this guide I will attempt to go through the basic process to go through when your hackintosh isn't functioning as it should.


### Boot Flags


Your bootloader, be it Clover, Chameleon or Chimera, will have certain flags or special instructions that tell it how to properly boot the machine. In this section, I'll go over some common boot flags and their uses.


#### -v Verbose Mode


This flag will cause your machine to boot in verbose mode. It will print information to the screen as it boots up, rather than displaying the apple logo. This is the go to method for determining why your machine hangs at the apple logo, and many advanced users prefer to boot this way normally.

If your machine hangs on a specific line of the verbose output, you can Google that line for more information about it. If you are asking for help because your machine will not boot, it is good practice to take a picture of your verbose output and post it along with your question.


#### -x Safe Mode


If you have experience with Windows, then you'll already know more or less what safe mode is. It boots your machine with only the essential drivers (kexts) required for the machine to work. This is useful for 2 main reasons. First, if your machine does not boot up in verbose mode and you cannot figure out why, safe mode can deduce whether or not it is an issue with your machine's core functions. Secondly, safe mode can be useful for recovery purposes. If you install a kext that breaks your system, you can boot into safe mode and remove it.

If you are having issues booting your machine, you should generally try safe mode just to see if it works, and because debugging a running machine is a lot easier.


#### UseKernelCache=No / Yes (10.8+)


The kernel cache is disabled by default, but can be used to speed up boot times by loading your kexts from a cache. If this doesn't work properly, OS X can boot extremely slowly.

Note: for before 10.8 (lion) use -f


#### darkwake=0


This flag disables an advanced power management feature of OS X, which allows some parts of the machine to wake from sleep, but this can mess up sleep on hackintoshes. Try this flag if your machine cannot sleep, or cannot wake from sleep. Alternativly darkwake=1 can enable the feature.

Note: your machine must be able to sleep through a DSDT or native means before this will make any difference.


#### PCIRootUID=1/ PCIRootUID=0


This flag can help fix hangs at boot. PCIRootUID=0 generally is needed if you're using an AMD graphics card.

Note: this flag solves issues related to graphics cards so you may have to use it upon initial installation or after changing GPU's.


#### ncpi=0x3000 / ncpi=0x2000


If your machine hangs around the line [PCI Configuration Begin], try both of these flags. 0x3000 is the standard fix, but 0x2000 can be tried if the first option fails to solve the issue.


#### dart=0


This disables some older visualization technology, VT-d. This can fix some motherboard issues, and will not inhibit applications like Virtualbox or Parallels as these applications use VT-x instead.


#### cpus=1


This flag can be used to boot with only a single core of your processor. It can be useful for getting some unsupported cpus to boot the installer.


#### arch=i386 / x86_64


These flags boot your machine into 32-bit mode (i386) and 64-bit (x86-64), the default for 10.6+ This mode may help with compatibility on some older machines.


### Clover Specific Boot Flags


The following boot flags should only be used in the Clover bootloader. They are fairly advanced.


#### MountEFI=yes/diskX


If your system cannot find your EFI partition, this flag can be used to denote which disk it is on. X refers to the disk number which I believe starts at 0 in the order that the bootloader sees the disks.


#### LogLineCount=0


This specifies the number of lines of log that clover will save before deleting them. 0 means it will save the log forever and is useful if your debugging your machine.


#### LogEveryBoot=Yes / No


This command will save Clover's logs every time the machine boots. I recommend you just leave this on so you'll have some point of reference if something breaks.


#### LogLocation=PATH


Set the location of the Clover logs. The default location should be in the root of your EFI directory.


### Chameleon/Chimera Specific Boot Flags


These flags are meant only for Chameleon/Chimera. Some of them might work in Clover, as it's documentation isn't exactly complete; however, most will not.


#### GraphicsEnabler=Yes / No


This kext enables many partially supported graphics cards through injection. It is not needed for 7xx and 6xx Nvidia graphics cards, but most others will need it. [Clover handles this issue through the config file]


#### IGPEnabler=Yes / No


This is an alternative to Graphics enabler. It can be used if you wish to use integrated graphics in conjunction with an Nvidia 6xx or 7xx card.




### Kernel Panics


Kernel panics are terrifying errors where the kernel doesn't hang at boot, it panics. This results in a rather frighting screen shown below.

![TS3742_01_KP-001-en](/images/guide-images/TS3742_01_KP-001-en.jpg)


If this happens, then you have a very serious problem. However, it may be fixable. The main reasons for this happening are incompatible CPU's and [Bios settings](http://www.skylineosx.com/installation/bios-configuration/), incompatible graphics or DSDT/config.plist errors. In this case, you'd want to double check all your components and settings. Googling '[part name] hackintosh' is generally a good start.

If you narrow it down to graphics card issues, you may want to do the initial installation on integrated graphics. You can then add and debug the graphics card later.

Should your machine kernel panic after booting for a while, you may have an issue with a higher function. If this is the case, you should see some grey text output behind the kernel panic dialogue. This is like a verbose output. You can use it to figure out what went wrong. If you cannot make heads or tails of the output or do not have the experience to understand it, Googling each line could provide you with an answer if it is a common problem.


### Asking The Right Questions


A lot of times, especially if you are new to hackintoshing you may need to ask for help. Regardless of the site, there are a few things you can do to make it easier and more likely for people to help you.



	
  *  Post your specs. Nearly every problem in hackintoshing relates to the hardware, so specs are necessary for anyone to help you.

	
  * Try basic boot flags. The generic ones listed above -v, -x and ncpi should all be tried in general situations, and if you see one that relates to your problem, give it a shot.

	
  * Post verbose or kernel panic output. If your machine panicked or hung, no one can really help without this.


Another simple thing to do when faced with these issues is to educate yourself. You can google most hackintosh related things and all of my hacktoshing knowledge has come from internet research. Check out [Additional Reources](http://www.skylineosx.com/additional-resources/) for more in depth info.


### Sources


www.macbreaker.com/2012/01/list-of-common-hackintosh-boot-flags_29.html

http://clover-wiki.zetam.org/Configuration/Boot

www.youtube.com/watch?v=IxtxWVj6kOk
