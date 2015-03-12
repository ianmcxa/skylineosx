---
author: ian_mcxa
comments: true
date: 2014-01-11 18:29:50+00:00
slug: enable-trim-on-your-ssd
title: Enable TRIM
permalink: /enable-trim
---

If you have a solid state drive, you will want to enable [Trim](https://en.wikipedia.org/wiki/TRIM), a protocol that speeds up SSDs. By default, Apple blocks trim on all non apple branded SSDs. There are two methods for enabling trim on a Hackintosh using Clover.


### Use The Trim Enabler App


This method is about as straightforward as they come. The only downside it's not the most vanilla looking.

Simply download the [Trim enabler app](http://www.groths.org/software/trimenabler/), click enable trim and reboot.


### Patch IOAHCIBlockStorage


This method is slightly more complex, but it is more vanilla and doesn't rely on 3rd party apps.

Open the Clover Configurator.

Load your config.plist by going File->Open->/EFI/EFI/CLOVER/config.plist

Under Kernel and Kexts Patches add a row to Kexts To Patch and enter the following:

Name: IOAHCIBlockStorage

Find* [HEX]: QVBQTEUgU1NEAA==

Replace* [HEX]: AAAAAAAAAAAAAA==

Save the config file and reboot.


### Confirm That TRIM Is Working


Go to the apple menu->About This Mac. Click More Info and then click System Report. Click SATA/SATA express

![Trim is working](/images/guide-images/trim-is-working1.jpg)

TRIM support should now say Yes.
