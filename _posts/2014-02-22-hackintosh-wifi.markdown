---
author: ian_mcxa
comments: true
date: 2014-02-22 07:10:47+00:00
layout: post
slug: hackintosh-wifi
title: Hackintosh WiFi
categories:
- Fixes
- General
- Hardware
- OS X
---

OS X is compatible with a select few wifi chips, so you will most likely have to buy a new wifi adapter. Most of them are fairly inexpensive though.

Note: There is one[ 802.11ac chipset that currently functions in OS X](http://www.skylineosx.com/getting-802-11ac-working/).


## Desktops


![](/images/guide-images/wifi1.png)

Some motherboards include wifi chips; however, for OS X compatibility you will need a PCI wifi card.

[TP-LINK TL-WDN4800](http://www.amazon.com/gp/product/B007GMPZ0A/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B007GMPZ0A&linkCode=as2&tag=sk0fc-20&linkId=JQY2AMTU7DSQLYL7) This is pretty much the standard OS X desktop wifi solution. It works out of the box with 10.7+

[TP-LINK TL-WN951N]("http://www.amazon.com/gp/product/B0034CL2ZI/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B0034CL2ZI&linkCode=as2&tag=sk0fc-20&linkId=DW2IRU47YMVKE6PX) This is a much cheaper card; however, it has only been certified to work with 10.9. You will also need to install this [patched kext](http://104.236.67.241/wp-content/uploads/2014/02/IO80211Family.kext_.zip).

If you have Snow Leopard, you will most likely have to purchase a discontinued WiFi card. Check the [OSX86 wiki](http://wiki.osx86project.org/wiki/index.php/HCL_10.6.8#Wireless) for details.

It is also possible to build your own wireless adapter out of a real apple airport card; see [this guide](http://x86wifi.blogspot.com/2010/04/how-to-build-your-own-real-airport-card.html). Self build adapters are often the most reliable and cost effective.


## Laptops


![](/images/guide-images/wifi2.png)

Nearly all laptops ship with wireless cards that must be replaced to get WiFi on OS X. Laptops use Mini-PCIe cards and Half Mini-PCIe cards. Make sure you know which type your laptop uses.


#### Mini-PCIe


[Atheros AR5BXB112 AR9380](http://www.amazon.com/gp/product/B009B5A0F0?ie=UTF8&camp=1789&creativeASIN=B009B5A0F0&linkCode=xm2&tag=sk0fc-20) This is an actual Apple Airport Extreme card. It will work out of the box. I'm not sure how far back it is compatible, but it should at least go to 10.6.

[Atheros AR5B91](http://www.amazon.com/gp/product/B00932XF6W?ie=UTF8&camp=1789&creativeASIN=B00932XF6W&linkCode=xm2&tag=sk0fc-20) This card will work out of the box with OS X 10.6+ and onwards.


#### Half Mini-PCIe


[Broadcom DW1510](http://www.amazon.com/o/ASIN/B002OB0FPI/sk0fc-20) This card has been tested working out of the box for 10.5-10.8 and should work with 10.9 as well.

[Atheros AR5B95](http://www.amazon.com/o/ASIN/B005HMZ8B2/sk0fc-20) To enable this card, you will need to install [this kext](http://www.osx86.net/files/file/738-atheros-ar5b95-ar5b95h-ar5b95-h-atheros-9285/). The card has been tested on 10.8 and should work on 10.9 as well.


## USB


![](/images/guide-images/wifi3.png)

Of course if you don't want to mess with PCI cards, you can always use a USB wireless adapter. They will generally be slower that PCI cards.

[D-Link DWA-131](http://www.amazon.com/o/ASIN/B002VJL0OI/sk0fc-20) This card will work with [Realtek's drivers](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU). You will have to start them at boot, so your wireless will load slightly more slowly. It works for 10.6-10.8 and should also work on 10.9.

[TP-LINK TL-WN727N](http://www.amazon.com/o/ASIN/B0035GU3QM/sk0fc-20) The wn727n requires a patched kext which has been tested on 10.6-10.8 and it should also work on 10.9. The kext should load faster than Realtek's driver; however, it is more likely to cause compatibility issues.

[TRENDnet TEW-648UB](http://www.amazon.com/o/ASIN/B002RL8I54/sk0fc-20) As with the D-Link, you'll need a [driver](http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1350) for this card. It is designed to work on 10.4-10.8 and should work on 10.9.


## Sources:


http://www.macbreaker.com/2012/04/most-compatible-wifi-cards-for-your.html

http://www.macbreaker.com/2013/08/the-best-usb-wifi-adapters-for-your.html

http://forum.osxlatitude.com/index.php?/topic/2120-supportedunsupported-wireless-cards-inventory/

http://wiki.osx86project.org/wiki/index.php/HCL_10.9.1
