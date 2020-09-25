---
title: "Linux on Microsoft Surface"
date: 2020-02-15T19:22:59+01:00
pre: "<b>0x05 </b>"
weight: 1
tags: ["linux", "kernel", "microsoft-surface"]
categories: ["hacks"]
summary: "If you want to run Linux exclusively or as a dual-boot configuration with Windows&reg; on a Microsoft&reg; Surface device you came to the right place."
thumbnail: "/hacks/images/0x05-Tux.png"
thumbnailalt: "Linux Tux"
---

Many people believe that buying a Microsoft&reg; Surface device as a developer is a bad choice. Not only is Windows pre installed but you cannot just 
rip it off and install your favourite Linux distribution.  
I bought my Surface Book without having any idea how powerful and convenient Linux can be. Sketching together a simple script to 
automate a task or writing complex applications in Java or C, Linux will be your goto OS for developement (maybe MacOS if you got the money).
So I decided, I'll try to make it work on my Surface device and discovered, I am not the only one with this goal.  
In the following article I will try to give some useful tips and share my experiences.

### Overview

[Disable BitLocker](#disable-bitlocker)  
[Setup your partitions](#setup-your-partitions)  
[Install Linux Distribution](#install-linux-distribution)  
[Configurate boot-loader and SecureBoot](#configurate-boot-loader-and-sercureboot)  
[Install custom Kernel](#install-custom-kernel)    
[Conclusion](#conslusion)  


### Disable BitLocker

The first thing I noticed when I started to edit my partitions is, that Microsoft by default enables BitLocker on their Surface devices.  
BitLocker is a proprietary disk encryption feature and secures the main Windows System partition.  
In order to install Linux you have to disable the encryption, espacially if you are aiming to setup a dual-boot environment.  
To disable the BitLocker feature you can follow this [guide](https://www.dell.com/support/article/de/de/debsdt1/sln302845/aktivieren-oder-deaktivieren-von-bitlocker-mit-tpm-in-windows?lang=de#DisablingBitlocker)     

### Setup your partitions

With BitLocker out of the way, you can start setting everything up for the Linux install.  
If you want to get rid of Windows just skip this segment and jump to the next one, if you want a dual-boot setup 
you have to take a few extra steps.  

First of all you need to shrink your NTFS partition on which your current Windows OS runs on. __Make sure to backup any important data before proceeding.__  
I recommend leaving at least 40-50 GB for Windows. __Do not touch__ any of the other partitions Microsoft set up for the OS, they are important.  
If you need help with shrinking your system partition visit the [Windows support site on this topic](https://docs.microsoft.com/de-de/windows-server/storage/disk-management/shrink-a-basic-volume)  
Now everything is setup for the installation of your Linux distribution.

### Install Linux Distribution

First of all you need to choose a distribution, the choice is yours. After you came to decision, download the ISO-Image for your distribution and create 
a bootable USB-Drive (I recommend using [Rufus](https://rufus.ie/)).  
After you finished this step proceed to change the boot-order in your UEFI settings (click [here](https://www.laptopmag.com/articles/access-bios-windows-10) if you have trubble accessing the UEFI)
and reboot. You should now find yourself in a desktop environment of the Linux distribution you have chosen and be prompted the option to install it.  
From here on just follow the instructions and install your new Linux. Use the space on your disk you freed earlier to setup all partitions you need. 

### Configurate boot-loader and SecureBoot

At this point you should be pretty much good to go with your new Linux OS, but there may be some obstacles remaining. FIrst of all, if you are running dual boot and your Linux distribution 
does not set it's boot loader to the highest priority you have to go back to the UEFI and select the installed Linux boot-loader as your primary one. If you still got trouble 
regarding the booting process you might want to install `boot-repair` in Linux and setup everything properly. 
 
The other problem you will face, regarding the next step, is, that Microsoft enables SecureBoot by default, which does not allow to boot an unsigned kernel, you can disable it in the UEFI 
aswell. Just setting it to `Allow 3rd party applications` might do the trick aswell.  

### Install custom Kernel

After you got your booting processes sorted out, you may notice that the touch screen and some other Surface specific funtions are not working or behaving oddly. Luckily we do not have to 
fix any driver issues and bugs by ourselfs but we can install the [Jakeday Kernel](https://github.com/jakeday/linux-surface) which gives us most of the needed drivers and fixes for basically 
any Microsoft Surface device we need.  
The main repository got the pre-compiled modules for debian based (Ubuntu, Xubuntu, etc.) system ready, if you have chosen an Arch based distribution you can use [this](https://github.com/dmhacker/arch-linux-surface) repository for the compiled kernel aswell. 
If you are using neither Arch- nor Debian-based distributions you have to compile the kernel by yourself (for instructions see the README.md on the Jakeday Kernel's page).  
To install the new Kernel you can follow the step by step instructions provided on the Jakeday Kernel's README page on how to setup the kernel patches. 

### Conclusion

In conclusion I have to say, there is some work required to get Linux running on your Microsoft machine but in my opinion it is worth the hassle. You can learn 
a lot about Linux as well as Windows and get a better understanding of disk partioning. With the Jakeday kernel there is really not much left not working.  
The Wifi-module in my first-gen Surface Book bugs out after hibernation but that can be fixed by opening a terminal and restarting the wifi driver.  
Appart from this I have followed the above steps and initially installed Ubuntu and now Manjaro, both working flawless in a day by day envrionment with Manjaro 
having the advantage of being an Arch-based system which is easily customizable.  
I hope the experiences provided here may help you setup your own Linux environment on a Microsoft Surface machine. 



#### Sources

Tux (Linux penguin): [Larry Ewing](ewing@isc.tamu.edu) made with [GIMP](https://en.wikipedia.org/wiki/GIMP)
