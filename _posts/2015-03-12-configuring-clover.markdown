---
author: ian_mcxa
comments: true
date: 2014-01-09 03:29:14+00:00
slug: configuring-clover
title: Configuring Clover
permalink: /configuring-clover
---

Here's where the fun begins.

For this step you'll need:



	
  * A Computer running OSX (or a virtual machine)

	
  * The [Clover Configurator](http://www.hackintoshosx.com/files/file/49-clover-configurator/)

	
  * The Installer we created in step 1.


Download the Clover Configurator from the link above and install it.

In your applications folder open the Clover Configurator. Go to File>Open> /EFI/CLOVER/config.plist

The config file is where you will tell Clover how to run on your machine. Through it you can enable various features and fixes that the developers have built into Clover. The config file is similar to org.chameleon.boot in the Chameleon bootloader.

The configurations are going to be vastly different depending upon what components you have, so I will attempt to go over the essential settings for getting through the installation process.

Note: The full explanation of config.plist parameters can be found [here](http://clover-wiki.zetam.org/pages/Configuration/).


#### **ACPI**


![ACPI_installation](/images/installation/acpi.png)

A lot of these settings will help you fix glitches post installation, but for now you shouldn't really have to touch any of them. We will go ahead and enable SSDT generation. An SSDT is a file that contains a set of instructions for how the computer wakes and sleeps. To do this check the Generate P and C States buttons.


#### **Boot**


![Boot_installation](/images/installation/boot.png)

These are some of the boot flags which are similar to those in Chameleon. You will want to enable slide=0 as it fixes compatibility issues within Clover. If your system doesn't boot, you may need to use some others as well, but make sure you know what a flag does before enabling it. Some of the settings can damage your machine.

If you want to use virtualization and enable VD-T or intel virtualization technology, you will need the dart=0 flag.

Note: in OS X Yosemite you will need to manually open the config file and add the flag _kext-dev-mode=1_

This can be done by opening the config file and appending the line

_<string>kext-dev-mode=1</string_

after the line

<key>Arguments</key>


#### **CPU, Devices, Disable Drivers and Gui**


All of these can be left alone for now.


#### **Graphics**


![Graphics_Installation](/images/installation/graphics_installation.jpg)

Select _Inject Intel_ if you have integrated graphics. Select _Inject __Nvidia _or _Inject ATI_ if you have an discrete graphics card. Fully supported Nvidia cards (6xx/7xx) do not need any injection.

If you have an ATI card, it is recommended that you complete your install using integrated graphics and add your graphics card in post install.

Note: Some unsupported cards may require injected or custom EDID's or device ID's


#### **Kernel and Kext** **Patches**


![Kernel and Kext Patches_Instllation](/images/installation/kernel.png)

Selecting KernelCPU will fix Kernel Panics due to unidentified CPU models. This will not work for AMD or Pentium systems, those will need a patched kernel.

If you are using Haswell and have a motherboard with a locked MSR's (asus boards have this), checking KernelPM will patch the kernel to enable power management.

If you are not using Haswell, Selecting Asus AICPUPM will prevent kernel panics related to power management and locked MSR's by disabling the write functions of AICPM (Apple Intel CPU Power Management).

If your BIOS resets after every reboot, select AppleRTC which will fix this issue.


#### Rt Variables


![Rt Variable_Installation](/images/installation/rt-vars.png)

If you want iMessages and iCloud to work in Yosemite you must enter the ROM and MLB values from a real mac. Otherwise simply press the calculate button.

#### **SMBIOS**


This can be left blank for now, Clover will select the best SMBIOS based on your machine.

If you want to keep the serial number from a previous install, you can enter that under the serial number tab.


#### **System Parameters**


![System Parameters_Installation](/images/installation/sysparams.png)

You will need to check Inject System ID for the SMBIOS to be injected.

Change InjectKexts to 'Yes' For existing installs change InjectKexts to 'IfnoFakeSMC'

Hit CMD+S to save your config file and exit the Clover Configurator.

Now, Navigate to /EFI/EFI/CLOVER and copy the config.plist to the 'Files' folder on the root of your installer drive.

<br>
<a class="btn btn-frontpage" style="float:left" href="/create-your-installer">Create your installer <i class="fa fa-chevron-left"></i></a>
<a class="btn btn-frontpage" style="float:right" href="/bios-configuration">Bios Configuration <i class="fa fa-chevron-right"></i></a>
