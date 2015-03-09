---
author: ian_mcxa
date: 2014-01-11 14:17:32+00:00
title: Tools for Hackintoshing
permalink: /tools-for-hackintoshing
---

There are a lot of tools out there for Hackintoshing. This guide will hopefully let you know what is what.


### Bootloaders: Clover vs. Chameleon


To run OS X on a PC you need a special bootloader. There are three bootloaders commonly used for hackintoshes.

**Chimera -not ****recommended**: Chimera is perhaps the most widely used hackintosh bootloader. It is supported by the Tonymacx86 forums. Chimera is, however, simply a repackaged version of Chameleon.

**[Chameleon](http://www.insanelymac.com/forum/files/file/59-chameleon-22-svn/)**: Chameleon is the most user friendly bootloader. It, and it's offshoot Chimera, are used my the majority of the Hackintosh community meaning it will be easy to find support and fixes for Chameleon.

**[Clover](http://sourceforge.net/projects/cloverefiboot/files/)**: Clover is a much more advanced bootloader than Chameleon. It automatically injects SMBIOS, and can quickly patch and fix many of issues with hackintoshes. Clover also supports UEFI booting, meaning faster boot times on UEFI capable motherboards. The issue with Clover is that the developers are primarily Russian and as such english documentation is not as easy to find. However, with this site I am hoping to expand the knowledge of Clover so that more people may see it as a viable alternative to Chameleon/Chimera.


### Installation Methods


There are a few scripted installers designed to make the Hackintoshing process easier. 

**[MyHack](http://myhack.sojugarden.com)**: Myhack is the most advanced scripted installer. It is also extremely easy to use, with support for MBR partitions. Myhack uses the Chameleon bootloader.

**Unibeast/Multibeast -not ****recommended**: Tools developed by Tonymacx86, these are probably the most commonly used and well supported in the hackintosh community. They use Tonymac's Chimera bootloader and are designed primarily for Tonymac's recommended builds.

**[Manual Installation](http://skylineosx.wordpress.com/installation/create-your-installer/)**: This is always a bit tricker than either of the above mentioned tools; however, I recommend that everyone do this because it allows for more flexibility, and if something goes wrong you will know exactly where and hopefully exactly why. Currently a manual install is the only way to get the Clover bootloader.

**[Hackintosh Vietnam](http://www.osx86.net/files/file/3842-hackintosh-vietnam-ultimate-aio-tool/)**: this isn't a complete install method; it's a post installation tool that helps you easily install kexts and configure your bootloaders.
