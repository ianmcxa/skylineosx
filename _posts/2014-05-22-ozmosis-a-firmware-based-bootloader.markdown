---
author: ian_mcxa
comments: true
date: 2014-05-22 01:26:08+00:00
layout: post
slug: ozmosis-a-firmware-based-bootloader
title: Ozmosis, a firmware based bootloader
wordpress_id: 710
categories:
- bootloader
- General
- Hardware
- OS X
post_format:
- Image
---

![](/images/guide-images/2012-09-24-17.06.31PIX.jpeg)

Generally when your machine boots, the firmware (UEFI or BIOS) looks to the hard drive to trigger the boot-loader. However, Apple Mac's have a special boot-loader stored in their firmware along with the UEFI. Because of this, the OS X installer does not include a boot-loader on it's own. To get around this, hackintoshers install Clover or Chameleon with custom installers, but there is a way for us to get our own firmware based boot-loader.

[ProjectQ](http://quocomputer.com/projectq/), a Kickstarter project from a while back, aimed to create a motherboard with a firmware boot-loader capable of loading any OS. They ended up creating the Ozmosis firmware, which if loaded into a motherboard would allow vanilla OS X to function as if it is being used on a real mac. This includes using an unmodified installer.

There are two ways to get the Ozmosis firmware.



	
  * Purchase the [ProjectQ](http://quocomputer.com/shop/z77mx-quo-aos/) motherboard (based on a Gigabyte motherboard)

	
  * Insert the Ozmosis firmware into your motherboard's firmware




### Inserting Ozmosis into motherboard firmware


The advantage of this is that you can use the normal OS X installer and you can upgrade from the app store as normal; however, the disadvantages are that it is extremely difficult and a bit dangerous. If fact, it's not really recommended unless you have some extra time, dual UEFI and want an extremely vanilla hackintosh.

The main issue when playing with firmware is that if something goes wrong there is nothing to fall back on. If you botch your OS X installation you can always reboot to the UEFI and start over, but if you mess up your UEFI there is nothing left to fall back on.

Some boards get around this issue by shipping with dual UEFI, in which a hardware switch toggles between two firmware chips. If you brick one chip, you can boot from the other and restore the original. In fact, if you do not have this feature, you really should not be messing with your firmware.


#### Guides


[http://www.projectosx.com/forum/index.php?s=3edd6ae429316bd40e1594406724373e&showtopic=3018](http://www.projectosx.com/forum/index.php?s=3edd6ae429316bd40e1594406724373e&showtopic=3018)

[http://www.osx86.net/topic/20657-ozmosis/](http://www.osx86.net/topic/20657-ozmosis/)


### Other Sources


http://www.insanelymac.com/forum/topic/291655-ozmosis/

http://quocomputer.com/
