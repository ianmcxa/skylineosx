---
author: ian_mcxa
comments: true
date: 2014-01-21 16:25:56+00:00
layout: post
slug: fix-valid-dvd-drive-could-not-be-found-70012
title: Fix Valid DVD Drive could not be found [-70012]
categories:
- Fixes
- Hardware
- OS X
post_format:
- Image
tags:
- '-70012'
- blue ray
- dvd drive
- Hackintosh
- Mac
- not valid
- osx
---

Last night I was attempting to watch Wrath of Khan on my hackintosh. Upon loading the DVD I was prompted with the following error: "Valid DVD Drive Could Not be Found [-70012]" I did some searching, and I found a fix courtesy of the Insanelymac forums.

The OS X dvd player app runs off of the DVDPlayback framework file, which is not designed to handle anything but Apple DVD drives. You can fix this by either using a different DVD playing app, or by patching the DVDPlayback framework.

Note: if you have an error related to an external DVD drive please check out [http://reviews.cnet....070591-263.html](http://reviews.cnet.com/8301-13727_7-20070591-263.html)


### Patching DVDPlayback


First we will backup the file that needs to be edited using the following terminal command:

You will need to enter your root password when prompted.

_sudo cp /System/Library/Frameworks/DVDPlayback.framework/Versions/A/DVDPlayback /System/Library/Frameworks/DVDPlayback.framework/Versions/A/DVDPlayback.bak_

Next we will patch the framework

_sudo perl -pi -e 's|x49x6Ex74x65x72x6Ex61x6C|x45x78x74x65x72x6Ex61x6C|g' /System/Library/Frameworks/DVDPlayback.framework/Versions/A/DVDPlayback_

Your DVD drive should now function as normal.


### Reverting the Framework if something goes wrong


Should something go horribly wrong in this process, you can always revert the DVDPlayback to it's original state. This could happen if you messed up the second terminal command.

_open /System/Library/Frameworks/DVDPlayback.framework/Versions/A_

Now, delete DVDPlayback and rename DVDPlayback.bak to DVDPlayback.


### Source


http://www.insanelymac.com/forum/topic/280858-dvd-drive-not-valid/
