---
author: ian_mcxa
comments: true
date: 2014-04-19 03:50:50+00:00
layout: post
slug: getting-802-11ac-working
title: Getting 802.11ac Working
categories:
- Fixes
- General
- Hardware
- OS X
tags:
- 802.11ac
- asus
- hardware
- wifi
---

In OS X Mavericks there is kext support for for the Broadcom bcm4360 chipset, which is an 802.11ac chipset. This means that any bcm4360 based adapter _should _function in OS X. This isn't always the case though.

There is an Asus card that some people have managed to get working.

[ASUS pce-ac68](www.amazon.com/o/ASIN//B00F42V83C/sk0fc-20)

In some cases the card works out of the box, however, there is a fix that can be applied if it shows up as an 'unknown card.' Note that this will require root privileges.

In the Terminal, type:

_sudo perl -pi -e 's|x30x6Bx10x00x00x75x0D|x30x6Bx10x00x00x90x90|' /System/Library/Extensions/IO80211Family.kext/Contents/PlugIns/AirPortBrcm4360.kext/Contents/MacOS/AirPortBrcm4360_

_sudo touch /System/Library/Extensions**/**_

Wait 30 seconds and then reboot your machine.

The wireless interface should then show up as 3rd party wifi and you should get 802.11ac speeds.

If you have had success with any other 802.11ac cards, please let us know.


#### Sources


http://www.insanelymac.com/forum/topic/289922-anyone-got-any-pci-e-bcm4360-wifi-ac-card-going-new-macbook-air-owner-wanted/
