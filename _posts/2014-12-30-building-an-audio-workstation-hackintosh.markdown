---
author: ian_mcxa
comments: true
date: 2014-12-30 01:44:56+00:00
layout: post
thumbnail: /images/guide-images/audio_workstation.jpeg
slug: building-an-audio-workstation-hackintosh
title: Building An Audio Workstation Hackintosh
---

![](/images/guide-images/audio_workstation.jpeg)

I'm going to do a series on Hackintoshes designed for a specific purpose. Since one of my other hobbies is [making music](http://ianmcxa.bandcamp.com/), I thought it would be fitting to start with a machine designed to be an audio workstation.

At the end of the guide is a zip archive with all the kexts and tools for this build.


#### CPU


Modern synthesizers take a good bit of CPU power, so you will want a top of the line CPU in your audio workstation.

[i7-4790](http://www.amazon.com/o/ASIN/B00J56YSLM/sk0fc-20)

[i7-4790k](http://www.amazon.com/o/ASIN/B00KPRWAX8/sk0fc-20) Only buy the unlocked model if you are going to overclock.


#### Motherboard


For an audio workstation, you're going to want a motherboard with lots of I/O ports and PCI slots so you can expand as needed.

[Gigabyte z97x-ud5h](http://www.amazon.com/o/ASIN/B00KYCSCVS/sk0fc-20)


#### Graphics Card


A super high end GPU isn't critical in an audio machine, but you still want to be able to handle running 2 or 3 monitors at 1080p. I've seen some builds recommending integrated graphics for an audio workstation, but that isn't ideal because you are running your graphics through the CPU's power.

[EVGA GTX 750](http://www.amazon.com/o/ASIN/B00IDG3NDY/sk0fc-20) This card will require the Nvidia web drivers to work in OSX, but it's very well suited to this build.


#### Memory


If you plan to do anything with sampled libraries or high quality exporting, you will want 16gb of RAM.

[Corsair Vengence 16GB](http://www.amazon.com/o/ASIN/B006EWUO22/sk0fc-20)


#### Storage


I recommend using an SSD for your applications and operating system; however, you should not run projects from an SSD as the large volume of reads and writes can wear out an SSD fairly quickly. In other words you will want to keep these two volumes separate, so don't set up a fusion drive.

[SanDisk 128GB SSD](http://www.amazon.com/o/ASIN/B007ZW2LY4/sk0fc-20)

[Western Digital Black 2TB HDD](http://www.amazon.com/o/ASIN/B00FJRS628/sk0fc-20)


#### Power Supply


Techniclly this machine should run at about 400-450W, but given that it's not too much more expensive it's a better idea to get a higher power PSU in case you want to add more devices later.

[Corsair 600W PSU](http://www.amazon.com/o/ASIN/B0092ML0OC/sk0fc-20)


#### Audio Interface


You won't want to  use the built in audio interface for high end audio work. Your choice of interface is going to depend a lot on what your needs are. I don't do much recording so all I need is outputs for my monitors and input for my midi devices. The general rule with these is that if they support OSX they'll work.

Here are some recommendations for smallish studio setups.

[Focusrite Scarlett 2i2](http://www.amazon.com/o/ASIN/B005OZE9SA/sk0fc-20)

[M Audio M-track](http://www.amazon.com/o/ASIN/B00BQ6KSN6/sk0fc-20)

[M Audio M-track QUAD](http://www.amazon.com/o/ASIN/B00DP5AV1A/sk0fc-20)


#### Case


In an audio workstation a silent case is very much needed.

[Fractal Design Define R4](http://www.amazon.com/o/ASIN/B008HD3CTI/sk0fc-20)


#### CPU Cooler


One of the main noise sources in your machine is going to be the CPU cooler. Since we have a silent case in this build, using the stock cooler won't create too much noise; however, if you are after absolute silence I recommend using an cooler. This one was designed to make minimal noise.

[Noctua NH-D14](http://www.amazon.com/o/ASIN/B002VKVZ1A/sk0fc-20)


### Install Bundle


[Mega](https://mega.co.nz/#!L0MhjCDQ!G10IhNilau_ovVD7cUJZybVVd5GNFARvNNfg8as0Ljk)  [Dropbox](https://dl.dropboxusercontent.com/u/77881163/Audio%20Workstation%20Install.tar.bz2)

This is a bundle that has all the software and drivers needed to get this build up and running. It includes.



	
  1. The Clover Bootloader

	
  2. Clover Configurator

	
  3. FakeSMC

	
  4. Ethernet Kexts


Unzip the archieve to the root of your installer and just follow the [installation guide ](http://skylineosx.com/installation/create-your-installer/)

Note: This build uses a GPU that requires the Nvidia web drivers to function. See [RampageDev's guide for details.](http://www.rampagedev.com/?page_id=276&page=3)

Update: The GTX 750 also must be booted with the flag PCIRootUID=1. You can set it under the boot tab in the clover configurator.

Disclaimers:



	
  * I personally have not built this exact computer,

	
  * The product links are amazon referral links that earn me a 4% commission. They help pay for Skyline's server.




### Sources


http://wiki.osx86project.org/wiki/index.php/HCL_10.10.1

http://www.tomshardware.com/forum/270453-28-best-digital-audio-workstation

http://www.tomshardware.com/forum/355597-28-looking-silent-tower-case

http://www.rampagedev.com/?page_id=276
