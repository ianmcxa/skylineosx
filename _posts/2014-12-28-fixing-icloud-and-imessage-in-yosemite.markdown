---
author: ian_mcxa
comments: true
date: 2014-12-28 01:11:44+00:00
layout: post
slug: fixing-icloud-and-imessage-in-yosemite
title: Fixing iCloud and iMessage in Yosemite
thumbnail: /images/guide-images/icloud-676x451.jpeg
categories:
- bootloader
- Fixes
- Guides
- OS X
tags:
- iCloud
- iMessage
- Yossemite
---

Apple has changed their identification methods when connecting to their online services including iMessage or iCloud. This means that most of the fixes you see online do not work anymore.  You will need access to a real mac for this to work correctly. Hopefully the Insanelymac guys will figure out a way to do this without a real mac soon.

This guide is designed to work with Clover. Before you begin, make sure you are running the latest version of the Clover Bootloader.


### 1. Insure than your NVram is functioning


NVram is a small bit of memory that is not reset upon reboot. Apple macs come with this function by default, but hackintoshes can require a few more steps.

Open the terminal and input the following commands:


<blockquote>

> 
> sudo nvram TestVar=TestVal nvram -p 
> 
> 
</blockquote>


You should see _TestVar  TestVal_ printed out.

Now reboot your machine and enter


<blockquote>nvram -p</blockquote>


If you still see TestVar  TestVal printed out then you're NVram is working properly, and you can skip to step 3.


### 2. Enabling NVram


![clover-settings-nvram](/images/guide-images/clover-settings-nvram.jpg)

Run the Clover installer on your boot partition selecting only to install the RC scripts on target volume. The optional RC scripts may help as well, so I suggest installing them as well.

The script will simulate NVram by writing the NVram values to disk at shutown and loading them at boot.


### 3. Insure your network adapter is set to en0


Apple Services will only work if your ethernet adapter is identifying as en0. Type the following command into the terminal to check your network interfarces


<blockquote>ifconfig</blockquote>


![ifconfig](/images/guide-images/ifconfig.jpeg)

You're output will look different depending upon the network hardware you have installed. The important part is that your active adapter be set to en0. If this is not the case, you will need to reset your network configuration, otherwise skip to step 5.


### 4. Reset Your Network Configuration


Navigate to the the network configuration directory. This can be done with the following terminal command


<blockquote>open /Library/Preferences/SystemConfiguration</blockquote>


Backup and delete the following configuration files.

Note: you can backup configuration files by copying them to your desktop.



	
  * Com.apple.airport.preferences.plist

	
  * Com.apple.eapolclient.configuration.plist

	
  * NetworkInterfaces.plist


Remove the folder CaptiveNetworkSupport

Now open System Preferences > Networking and remove all your network interfaces using the minus button. Make sure you write down your VPN configurations or static IPs if you have any, before removing them.

![ethernet-settings](/images/guide-images/ethernet-settings.png)

Now, Reboot your machine and add the interfaces back using the plus button. Make sure you add your ethernet interface first. You should only have to add back ethernet/wifi and VPN interfaces.

Now check your interfaces with ifconfig again. Your ethernet card should now register as en0.


### 5. Inject A Correct Serial Number


Open the [Clover Conigurator](http://www.hackintoshosx.com/files/file/49-clover-configurator/) and mount your UEFI partition using the provided button.

Open your configuration file located in EFI/EFI/CLOVER/config.plist

Under the SMBIOS tab, click the wand button. Select the correct SMBIOS (usually an iMac with similar a similar processor to yours) You can see what your SMBIOS is currently set to under About This Mac.

![smbios1](/images/guide-images/smbios1.jpeg)

Next, click the shake button for the Week of Production and unit number

Go to[ https://selfsolve.apple.com](https://selfsolve.apple.com) and enter the serial number you generated. If the site does not give you an error, click the shake button again and generate a new serial. The reason for this is that you want a unique serial that is not being used by another mac. Once you get a serial number that generates an error, click OK.

Now open a terminal window and type


<blockquote>uuidgen</blockquote>


Copy the output into smUUID. Your screen should now look similar to this

![smbios2](/images/guide-images/smbios2.jpeg)]

Now we need a a Board Serial Number. This can be created by taking the serial number and adding 5 digits, for example if your serial is C02LHIA7DNX1, your board serial number could be C02LHIA7DNX1**7E884**. Remember, the board serial number _must_ be 17 digits long.


### 6. Inject A Correct MLB and ROM Identifier


This is the tricky part. Apple has changed their verification process to only allow valid MLB (main logic board) and ROM identifiers. This means that you need to extract these values from a real mac.

Now you will need values from a real mac. It does not matter what model of mac you are using. Using the values will not cause any problems for the real mac.

Note: You should not use any values you find online as that could get your apple ID deactivated.

On a real mac, download and run the tool [Apple Mac Hack](http://applemac.tools.greenosx.com/guide/) You should see something similar to this. Do not press the generate button.

![id-fake](/images/guide-images/id-fake.jpeg)


At this point we are done with the real mac.

On your hackintosh, navigate to the Rt variables tab and fill in the appropriate boxes. Omit the colons in the ROM. Make sure you use UPPERCASE letters as lowercase letters will cause errors when attempting to sign in.

![rt vars](/images/guide-images/rt-vars.jpeg)

Now make sure all fields in System Parameters are blank, save your Clover configuration and exit.

Disconnect your hackintosh from the internet and reboot.

Once you have reconnected to the internet you should be able to sign into iMessage and iCloud. If you have any issues, or if you find a way to generate valid MLBs without a real mac please don't hesitate to leave a comment.


### Sources


http://www.insanelymac.com/forum/topic/303073-pattern-of-mlb-main-logic-board/

http://www.insanelymac.com/forum/topic/298027-guide-aio-guides-for-hackintosh

http://www.insanelymac.com/forum/topic/302347-clover-imessagefacetime-fix-for-yosemite/

http://applemac.tools.greenosx.com/guide/
