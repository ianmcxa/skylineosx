---
author: ian_mcxa
comments: true
date: 2014-02-08 01:57:12+00:00
layout: post
slug: editing-about-this-mac
title: Editing 'About This Mac'
categories:
- General
---

When hackintoshing, the data displayed in 'About this mac' is simply the data from the model selected in the SMBIOS you selected upon install. Many times this isn't what you want displayed, so in this guide we will be cosmetically modding the about this mac tab. You can do this on both hackintoshes and real macs too.

This will in no way affect your system performance, and you can still see the information the system sees by clicking on 'System Profiler"

You will need:

For creating icons
[Download image2icon](http://static.shinyfrog.net/downloads/image2icon/Img2icns.zip)

For editing the text
[Download Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)

If you want to edit the hardware specs, you'll need Textwrangler
[Download](http://ash.barebones.com/TextWrangler_4.5.6.dmg)


### Editing the Text


Your mac contains a configuration file which loads the about this mac text data from the machine. We can override this and have it display whatever text we want.


#### Model Name, Year and Monitor Size


Open the terminal, copy the following line and press enter:

open ~/library/preferences/com.apple.systemprofiler.plist

If you have Xcode installed, it will open the file.

Note: do not edit these files with Text Edit.

[![Model Name plist](/images/guide-images/Model-Name-plist.jpg)


You can now Change DNMP-en_US to your desired text, I.E "Hackintosh (23-inch, 2013). I suggest you leave the parentheses because I don't know what would happen if you removed them.


#### CPU and Memory


Generally the specs listed by About This Mac should be correct. If they're not, then you may have a problem and I suggest research it to find out more. This guide is merely for those who want to change the specs cosmetically.

Open the terminal, copy the following line and press enter:

open /System/Library/CoreServices

Now find Loginwindow, right click on it and click Show Package Contents

From inside the package navigate to /Contents/Resources/english.lproj

Right click on AboutThisMac.Strings and open with Textwrangler

![AboutThisMac_Strings](/images/guide-images/AboutThisMac_Strings.jpg)

Change the <string> under ABOUT_BOX_MEMORY_FIELD_FORMAT to what you want under Memory, I.E. <string>16 GB 1600MHZ</string>

Change the <string> under ABOUT_BOX_MULTIPLE_PROCESSORS_FIELD_FORMAT to what you want your processor listed as.

Note: If you have an old single core system edit ABOUT_BOX_SINGLE_PROCESSOR_FIELD_FORMAT

For this file, you will want to save the update file to your desktop, backup the original and replace it with the file you just created.


### Editing the Picture


Under About This Mac, you'll have a picture of whatever model mac you picked in your SMBIOS. You can change this pic to whatever you like.

Get the picture of whatever you want in you About this mac tab. Note: case manufacturers generally have high resolution images of their cases on their website.

You will want to get the image in .png, .tif or .jpeg format.

![img2icns](/images/guide-images/img2icns.jpg)


Open Img2icns, drag the file onto the window, click ICNS and save the file to your desktop.

Now, go to the terminal and type the following:

open /System/Library/CoreServices/CoreTypes.bundle/Contents/Resources

Locate your SMBIOS icon, this will vary depending upon the SMBIOS that you are using.

Mac Pro = _com.apple.macpro.icns_

iMac 13,4 = _com.apple.imac-unibody-27-no-optical.icns_

The rest are petty easy to find. You can match the picture to the one in your SMBIOS if you need to.

Create a backup of your SMBIOS icon.

Rename your custom to the name of the SMBIOS one, and copy it into the Resources folder.

All changes should take effect upon reboot.


### Sources:


https://rampagedev.wordpress.com/os-x-tweaks/customize-about-this-mac-information-icons/

http://www.tonymacx86.com/customization/79536-mod-about-mac.html
