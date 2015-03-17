---
author: ian_mcxa
comments: false
date: 2014-01-24 10:46:51+00:00
layout: post
slug: running-os-x-on-windows-virtualisation
title: 'Running OS X on Windows: Virtualisation'
wordpress_id: 497
categories:
- Guides
- OS X
post_format:
- Image
tags:
- environment
- testing
- virtual
- virtualisation
- vps
---

Over at Skyline OSX we're all about building your own Hackintosh computers, but sometimes you might just not be that sure whether you really want to go for OS X. Or maybe, you just need it for some spare-time development tasks? This is why, sometimes the best option is to simply run OS X on Windows and we are going to be doing this right now, with the help of [glossary slug='seo' /] software.


## What is Virtualisation?


Virtualisation is a rather simple concept if you just scratch the very surface of it. Virtualising an Operating System (in this case OS X) means running the Operating System in question inside another operating system (such as Windows 7). Your primary operating system.


## The Setup


Before starting to do anything, we'll need a couple of things:



	
  1. VMware Player for Windows.

	
  2. VMware Unlocker for OS X by [Donk](http://www.insanelymac.com/forum/user/142645-donk/).

	
  3. OS X iso file.

	
  4. Some spare time.


[Download VMware Player](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/7_0)

You can simply Google for an OS X iso, or you can make a copy of a working OS X disc.


## Installation




### Unlock VMware





	
  * First off, we will need to set up the WMvare unlocker.

	
  * If you haven't downloaded it yet, go ahead and download it.

	
  * Extract the archive and navigate to the **windows** folder.

	
  * Right click **install.cmd** and select **Run as Administrator**. 




### VMware Configuration





	
  * Fire up VMware player.

	
  * Click **Create a New Virtual Machine**

	
  * Go ahead and select your OS X iso.

	
  * _In case it says "Cannot read this file." go ahead and select "I will install the operating system later"._

	
  * In the next screen, select the appropriate choices for your OS X installation, the **OS type** and the **version of OS X** being installed.

	
  * Go ahead and tweak your **hardware settings** in the next screen. If you have no clue, leave them at the recommended settings. Once everything's done there, close the box and click **Finish**.

	
  * You should now have Mac OS X in the list of your virtual operating systems.

	
  * Select **Mac OS X** and click on **Edit virtual machine settings**.

	
  * Select **CD/DVD** from the list and check the **Use ISO image file** option and choose your OS X image file.

	
  * Click **OK** and then go ahead and click on **Play virtual machine.**




### Installing OS X





	
  * You should be greeted by the **OS X Utilities** screen. Go ahead and select **Disk Utility**.

	
  * Select your **VMware Virtual Hard Disk Drive** from the list on the left-hand side.

	
  * Go to the **Partition tab** and select **Partition 1** on the **Partition Layout** option.

	
  * Name it however you want it and click **Apply**.

	
  * Once the partitioning is done, **close the Disk Utility**.

	
  * Select **Reinstall OS X** from the list and simply install OS X by completing the standard procedure of clicking Next and Agree to everything the installer asks for.


That's it! You can now enjoy your virtualised version of OS X. 
