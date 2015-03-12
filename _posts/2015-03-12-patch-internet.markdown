---
author: ian_mcxa
comments: true
date: 2014-01-11 16:15:01+00:00
slug: internet
title: Internet
permalink: /patch-internet
---

Unless you are extremely lucky, you will need a kext to enable your internet. Most ethernet built into motherboards can be used; however, a very small number of wifi cards are supported. If you have a prebuilt system or laptop, most likely you will have to purchase a new wifi adapter.


### Wifi Cards


For a list of compatible desktop wireless cards check out [Macbreaker's article](http://www.macbreaker.com/2012/04/most-compatible-wifi-cards-for-your.html).

For a list of compatible laptop wireless cards check out the [inventory at OSXlatitude](http://forum.osxlatitude.com/index.php?/topic/2120-supportedunsupported-wireless-cards-inventory/).


### Ethernet


Most likely you'll be able to use your motherboard's built in ethernet. First, find the type of ethernet card in your motherboard. This can be found in the manual or on the manufacturer's website.

[Intel Ethernet](http://sourceforge.net/projects/osx86drivers/files/Kext/Snow_Lion/AppleIntelE1000e.kext.zip/download) kext by Hnak [i[nsanelymac development thread](http://www.insanelymac.com/forum/topic/205771-appleintele1000ekext-for-108107106105/)]

[Atheros](http://www.insanelymac.com/forum/index.php?app=core&module=attach&section=attach&attach_id=115905) kext for AR81(31/32/51/52) by Shailua [[insanelymac development thread](http://www.insanelymac.com/forum/topic/283086-updated-atheros-ar8131325152-driver-for-107108/)]

[Realtek ](http://www.insanelymac.com/forum/files/file/88-realtekrtl8111-binaryzip/)RTL8111/8168 kext by Mieze [i[nsanelymac development thread](http://www.insanelymac.com/forum/topic/287161-new-driver-for-realtek-rtl8111/)]

**Note:** these are simply some of the most common ethernet kexts. If your motherboard uses a different chip for ethernet, it does not mean you can't get it working. You will, however, have to do some research. Check out [Osx86 Downloads](http://www.osx86.net/files/category/10-network/?sort_order=DESC&sort_key=file_submitted&num=10) and [Insanelymac Downloads](http://www.insanelymac.com/forum/files/category/5-lan-and-wireless/) for kexts. Not all the drivers are listed in the downloads section, so be sure to check the forums as well.

If all else fails, you can still purchase an ethernet PCI card.


### Installing the Kext


Once you have downloaded the kext, copy it to /EFI/EFI/CLOVER/kexts/10.10 Reboot to apply the changes.

**Note: **Injectkexts must be set to 'Yes' for this to work.
