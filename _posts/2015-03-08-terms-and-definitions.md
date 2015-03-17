---
title: Terms and Definitions
date: 2013-12-30
permalink: /terms-and-definitions
---
When starting out hackintoshing, there can be a lot of daunting terms and jargon. In this section, I will attempt to define many of these terms.


**Hackintosh** – A PC that has been ‘hacked’ to run Mac OS X.


**BIOS** (basic input/output system) – The BIOS is the first thing that launches when you start your computer. The bios is built into a chip on your motherboard. It is responsible for basic low level settings, over-clocking and starting the bootloader.


**SATA** (Serial ATA Connector) - This is the cable type and interface between your hard drives and motherboard.


**Bootloader** - The bootloader is a piece of software that is initiated by the bios. It allows you to select what drive or partition to boot to and starts the kernel.


**Clover** – Clover is a specialized bootloader that is capable of loading OS X on a hackintosh. It is an EFI (Extensible Firmware Interface) bootloader, which means that acts as a layer between your hardware and OS X.


**Kernel** – this is the core of your operating system. It manages your core system functions and is responsible for loading the rest of your operating system.


**Kernel Panic** - When the kernel is loading the operating system, sometimes things go wrong. A critical driver may be incompatible or your operating system may not be installed quite right. In this case your computer will display some text detailing what happened and shut down. When this happens, remain calm. Document the text output, get to a functioning machine and research the problem. It is likely someone else has had the same issue and there is a workaround or fix.


**Kext** (kernel extension) – Kexts are similar to Windows Drivers. They are modules loaded by the kernel that can add support for various things. When running OS X on a PC, you will need to add kexts to get full functionality out of your machine.


**UEFI** ([Unified Extendable Firmware Interface](https://en.wikipedia.org/wiki/Extensible_Firmware_Interface)) – UEFI is an alternative interface to BIOS. If your motherboard has this, you will have UEFI booting options. If you’re using Chameleon/Chimera, you must ignore these. If you are using Clover (and have installed for use with UEFI), you must select the UEFI boot options. UEFI allows for more compatibility and faster boot times than standard BIOS.


**Power Management** – This refers to your computer’s ability to use less power as needed. It enables sleep and speedstep, which dynamically controls how much power your CPU is using. On some hackintoshes, namely those without Gigabyte motherboards, a few kexts will need to be patched to enable power management features.


**DSDT** (Differentiated System Description Table) – This is an info file that tells your operating system how to interact with your hardware. It can be patched to add functionality in OS X.


**SMBIOS** – The SMBIOS or system definition is how Apple machine identify themselves. Because we are running OS X on a machine that is not made by apple and has no specific SMBIOS we have to select the closest match. Fortunately, Clover will do this for us. An OS X machine will behave slightly differently depending upon what kind of Apple computer it believes it is.
