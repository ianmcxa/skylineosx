---
author: ian_mcxa
comments: true
date: 2014-01-11 19:38:56+00:00
slug: fix-yellow-drive-icons
title: Fix Yellow Drive Icons
permalink: /patch-drive-icons
---

In some cases a glitch may occur that causes your internal drives to appear as external drives.

There is a simple fix for this using Clover.

Open the Clover Configurator. Load your config file from File->Open->/EFI/EFI/CLOVER/config.plist

![Fix Disk Icons](/images/guide-images/fix-disk-icons.jpg)

Under Kernel and Kext Patches, add a new row.

Name: AppleAHCIPort

Find* [HEX]: RXh0ZXJuYWw=

Replace* [HEX]: SW50ZXJuYWw=

Save the config file and reboot.
