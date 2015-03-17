---
author: ian_mcxa
comments: true
date: 2014-07-25 00:58:12+00:00
layout: post
slug: yosemite-now-in-public-beta
title: Yosemite Now in Public Beta
categories:
- General
---

OS X 10.10 is now in pubilc beta. You can sign up for the beta on [Apple's site](https://appleseed.apple.com/sp/betaprogram/). They will then email you with a code which you can enter in the App Store to download a copy of Yosemite. You must be running OS X mavericks for the code to work.

This is a newer build than any of the Developer Previews that have been previously released; however, our [guide for installing the DP1](http://www.skylineosx.com/yosemite-installation-guide/) should still work fine.

If you would prefer an easier way to create the usb installer,  Insanelymac forum member Snatch has created a script to automatically create the installer. You'll still have to install the bootloader + kexts though. To get access to the download you must register at Insanelymac and download the script from [this thread](http://www.insanelymac.com/forum/topic/298521-easy-yosemite-1010-usb-installer-updated-public-beta/).


#### Update:


Yesterday I decided to do something fairly risky. I upgraded to 10.10 using the native OS X installer. Fortunately everything went smoothly, so here's a little guide on how to do just that. Just please bear in mind that this is a bit risky and you shouldn't do it unless you know what you're doing and can recover if something goes wrong.

Make sure you are running the latest version of the clover bootloader.

Open your clover config file and add the lines.

_<key>Arguments</key>_
_<string>kext-dev-mode=1</string>_

Then create /EFI/Clover/kexts/10.10 and copy your kexts over to it.

Open the OS X installer and install on your hard disk.

When the machine reboots, select install OSX from [your hard drive name]

Note: If you do not usually boot with injected kexts I.E you keep your kexts in /S/L/E, then you will need to press space and select 'with injected kexts'

Yosemite should now install normally and you should be able to reboot to it.


#### Sources


https://appleseed.apple.com/sp/betaprogram/

http://www.insanelymac.com/_/apple/os-x-yosemite-public-beta-is-now-available-for-r1013

http://www.insanelymac.com/forum/topic/298521-easy-yosemite-1010-usb-installer-updated-public-beta/
