---
date: 2015-05-09
title: Enabling Bluetooth Handoff on A Hackintosh
tags: bluetooth, guides, osx, yosemite
thumbnail: /images/guide-images/handoff_title.jpeg
---
#What is Bluetooth Handoff?
Bluetooth Handoff is a feature is a feature of OS X 10.10 that allows you to pick up what you were doing on your iOS devices device with your mac. It works for Mail, Safari, iWork, Calendar and Contacts. Sadly it does not work by default on hackintoshes.
##Connecting iCloud
You must have iCloud working on your hackintosh to enable handoff. For more information see [Fixing iCloud and iMessage in Yosemite](/bootloader/fixes/guides/os x/2014/12/27/fixing-icloud-and-imessage-in-yosemite.html).

##Enabling Bluetooth
For Handoff to work at all, you first need bluetooth working on your hackintosh. Moreover, only certain bluetooth chips appear to be working with handoff. Here is a list of 

###Working Adapters

####[Azurewave AW-CE123H](http://www.amazon.com/o/ASIN/B00HRFS1GQ/sk0fc-20)

The Azurewave AW-CE123H works best with this patch. If you are buying a bluetooth adapter to use with handoff, get one of these. It will fit PCI-e slots on desktops and laptops.

[![](/images/guide-images/bluetooth4.png)](http://www.amazon.com/o/ASIN/B00HRFS1GQ/sk0fc-20)

####[ORICO BTA-402](http://www.amazon.com/o/ASIN/B00AKO7XOW/sk0fc-20)

The ORICO BTA-402 also works, but only with MacbookPro SMBIOS. The hotspot feature does not work with this adapter. I would only recommend using this one if you already have it, or if you _absolutely_ must have a USB adapter.

[![](/images/guide-images/bluetooth2.png)](http://www.amazon.com/o/ASIN/B00AKO7XOW/sk0fc-20)

See [Hackintosh Bluetooth](/2015/04/03/hackintosh-bluetooth.html) for more information.

#Enabling Handoff
Depending on your bootloader the steps to enable handoff will be different.
##Clover
If you use the Clover Configurator, you can simply add the following under *Kernel and Kext Patches*

![](/images/guide-images/bluetooth_patch.jpeg)

If you have not already done this, make sure kext\_dev\_mode is set to 1.

![](/images/guide-images/kext_dev_mode_1.jpeg)

You can also manually add the following lines to your clover config.
>`<dict>`

>`<key>Comment</key>`

>`<string>Enable Handoff</string>`

>`<key>Find</key>`

>`<data>4885C0745C0FB748</data>`

>`<key>Name</key>`

>`<string>IOBluetoothFamily</string>`

>`<key>Replace</key>`

>`<data>41BE0F000000EB59</data>`

>`</dict>`

Now sign out of iCloud, reboot and sign back in. Handoff should now work.
##Chameleon
The steps for chameleon are a little different.

Open a terminal and enter the following command.
> sudo cp -r /System/Library/Extensions/IOBluetoothFamily.kext /System/Library/Extensions/IOBluetoothFamily.kext.bak

This will make a backup copy of your IOBluetoothFamily.kext in case something breaks. 
Then type
> sudo perl -i.bak -pe 's|\x8B\x87\x8C\x01\x00\x00|\xB8\x0F\x00\x00\x00\x90​|sg' /System/Library/Extensions/IOBluetoothFamily.kext/Contents/MacOS/IOBluetoothFamily

Now sign out of iCloud, reboot and sign back in.

Should something go horribly wrong, you can revert your IOBluetoothFamily.kext using the following terminal command.

>sudo mv /System/Library/Extensions/IOBluetoothFamily.kext.bak /System/Library/Extensions/IOBluetoothFamily.kext



<hr>
_Disclaimer: I have not personally done this on my Hackintosh. I am not responsible if anything goes wrong._
##Sources
http://www.insanelymac.com/forum/topic/302410-patch-enabling-handoff-for-non-apple-bt4-devices

https://www.apple.com/osx/continuity/
