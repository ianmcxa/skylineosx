---
author: ian_mcxa
comments: true
date: 2014-01-11 17:52:35+00:00
slug: audio
title: Audio
permalink: /patch-audio
---

To enable audio on a hackintosh there are three basic options.



	
  * Use a patched version of AppleHDA.kext.

	
  * Use VoodooHDA, which works for almost all motherboards but is unstable.

	
  * Purchase a sound card that is natively compatible with OS X.




### Patched AppleHDA Method




#### Premade Realtek HDA Patches


[Realtek ALC885](http://www.insanelymac.com/forum/files/file/131-realtek-alc885-applehda-audio/)

[Realtek ALC887](http://www.insanelymac.com/forum/files/file/129-realtek-alc887-applehda-audio/)

[Realtek ALC888](http://www.insanelymac.com/forum/files/file/130-realtek-alc888-applehda-audio/)

[Realtek ALC889](http://www.insanelymac.com/forum/files/file/124-realtek-alc889-applehda-audio/)

[Realtek ALC892](https://github.com/toleda/audio_ALC892) **Note**: follow readme install guide. Kext will not be preserved upon update.

[Realtek ALC898](http://www.insanelymac.com/forum/files/file/164-applehda-for-alc898-109/)

[Realtek ALC1150](http://www.insanelymac.com/forum/files/file/143-applehda-for-alc1150-1091/) **Note**: requires DSDT patch. Your DSDT must be placed in /EFI/EFI/CLOVER/ACPI/patched for use with Clover.

More AppleHDA patches can be found at [Insanelymac](http://www.insanelymac.com/forum/files/category/4-audio/?sort_order=DESC&sort_key=file_updated&num=10) and [osx86.net](http://www.osx86.net/files/category/9-audio/).

It is also possible to patch AppleHDA for your audio chip yourself. This is an advanced topic. If you are interested, check out [this guide.](http://www.insanelymac.com/forum/topic/295001-guide-to-patch-applehda-for-your-codec/)


#### Installing Patched AppleHDA


Download the [Audio Kext Enabler](https://github.com/toleda/audio_kext_enabler) kext.

Copy your patched HDA and Audio Enabler kext to /EFI/EFI/CLOVER/kexts/10.9

Navigate to /System/Library/Extensions backup and delete the AppleHDA.kext located there. **Note: **You may have to redo this step after an update.

If in the process you cause your computer to kernel panic, boot to safe mode (-x) and restore the original AppleHDA.kext.


### Using VoodooHDA


VoodooHDA is compatible with more products but what it gains in compatibly it loses it reliability and quality. Most users are expected to have mixed results.

[Download Link](http://sourceforge.net/projects/voodoohda/)

To Install, copy the kext to EFI/EFI/CLOVER/kexts/10.9. Navigate to /System/Library/extensions. Backup and delete AppleHDA.kext and reboot.

[Here](http://www.insanelymac.com/forum/topic/267905-voodoohda-common-problems/) is a list of fixes for common VoodooHDA problems.


### Purchasing a USB/Firewire/PCI Sound Card


This is probably the most reliable option. I recommend that anyone working with audio or music production do this.

Any interface advertised as compatible with OS X should work. Just be sure that Firewire/USB3.0 are functioning if you get a card for them.

I use a Lexicon Alpha on my system and it worked completely OOB.
