---
author: ian_mcxa
comments: true
date: 2014-01-18 23:52:03+00:00
layout: post
slug: editing-clovers-config-plist
title: Editing Clover's config.plist
categories:
- General
post_format:
- Image
tags:
- .plist
- bootloader
- Clover
- Hackintosh
- Mac
- Slice
- UEFI
---

Clover is controlled by it's config file, and in all our other guides we have used the Clover Configurator, a gui app which can generate and modify your config.plist for you. There are times when you need to modify the config.plist directly.


### File Structure


The config.plist is structured like an XML file, and can be edited in much the same way. Check out the [clover wiki](http://clover-wiki.zetam.org/Configuration) for a full list of all Clover's parameters.


### [Xcode](https://developer.apple.com/xcode/)


Xcode is apples development and coding application. Once installed, you can double click your config.plist to bring up Xcode's plist editor.

![config.plist Xcode](/images/guide-images/config.plist-Xcode.jpg)

Through this editor you can add and remove values using the plus and minus buttons. You can set the type and the value of an item.


### [Textwrangler](https://itunes.apple.com/us/app/textwrangler/id404010395?mt=12)


Textwrangler lets you directly edit the config.plist just like an xml file.

![textwrangler config.plist](/images/guide-images/textwrangler-config.plist_.jpg)

This is especially useful when you want to incorporate some config file code from an online resource. When editing the file like this, it is very important to keep the code correctly formatted. A formatting error in the config file can prevent your system from booting.
