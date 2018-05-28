---
layout: post
title: "Installation and Configuration of Arch Linux"
comments: true
description: "Installation and Configuration of Arch Linux"
keywords: "Installation and Configuration of Arch Linux"
date:   2018-05-27 12:16:22 +0200
published: true
categories:
- Writing
---
![Arch Linux](https://uonai.space/images/arch-linux.jpg){:class="img-responsive"}
I bricked my Macbook Pro this weekend and took the opportunity to upgrade to a Windows 10 / Linux dual boot. I purchased a Lenovo T470 because it was rated well for both Linux and Windows and was built for buisiness-grade programming. 

Manjaro is the Arch Linux distro that I decided on [https://manjaro.github.io/](https://manjaro.github.io/). Arch Linux has a reputation for being difficult to configure and hard to maintain. However, Manjaro provides enough built-in functionality to make installation and maintenance less painful. I'll try to highlight my process for installing Arch Linux to make it easier for anyone looking to make the move. Note: I anticipate that everyone will have their own form of struggle, so be prepared to tinker.
 
# Step 1: Try out your Linux distro before installing.
Based on past experience spinning up VMs, I opted for Oracle VirtualBox. This let me get a feel for a couple different Linux distros: Solus, ElementaryOS, Ubuntu, Arch Linux. 

Process for setting up VM: [https://wiki.manjaro.org/index.php?title=VirtualBox](https://wiki.manjaro.org/index.php?title=VirtualBox)

# Step 2: Back up files.
I backed up the few files that I had locally by adding them to my Google Drive. Never know what can go wrong when installing new operating systems.

# Step 2: Free up space on your hard drive.
My hard drive on my Lenovo T470 is 250GB. I dedicated 150 to Windows 10, 100 to Arch Linux. To free up space, I followed this tutorial: [https://www.youtube.com/watch?v=9gS5SoogltE](https://www.youtube.com/watch?v=9gS5SoogltE)

# Step 3: Create Bootable USB drive.
Manjaro has three versions: XFCE (minimal), KDE (luxury), GNOME (halfway point between XFCE & KDE), Architect (console-based). Based on my specs, I installed KDE. After downloading the ISO, I followed this tutorial to set up a bootable USB stick with the ISO. Because I'm on Windows 10, I followed this section: "Writing to a USB Stick in Windows": [https://wiki.manjaro.org/index.php?title=Burn_an_ISO_File] (https://wiki.manjaro.org/index.php?title=Burn_an_ISO_File) 

# Step 4: Boot from BIOS, run Arch Linux installer.
There were a few Lenovo manufacturer that I needed to resolve here. I anticipate this will be different for each user based on manufacturer. You'll need to modify your BIOS settings to be able to boot from USB. Here are the updates I needed to make:

## Windows Updates
Disable fast startup: [https://lifehacker.com/enable-this-setting-to-make-windows-10-boot-up-faster-1743697169](https://lifehacker.com/enable-this-setting-to-make-windows-10-boot-up-faster-1743697169)

## BIOS Updates
I needed to make these updates to BIOS when I rebooted my PC. Prior to making these updates I was not able to boot from USB.
* SECURITY page
    * Secure Boot = Disable
* STARTUP page
    * UEFI/Legacy Boot = Both
    * UEFI/Legacy Boot / UEFI/Legacy Boot Priority = UEFI First
    * Boot device list F12 Option = Enabled

Once manufacturer issues are resolved (if you end up having any), you'll be able to install Manjaro. For the install, I followed this tutorial: [https://www.youtube.com/watch?v=4-kafKduFZw](https://www.youtube.com/watch?v=4-kafKduFZw)

# Step 5: Install packages. 

After installation was complete, I started installing packages for my dev environment. Mostly all packages in Arch Linux are installed through Pacman: [https://wiki.archlinux.org/index.php/pacman](https://wiki.archlinux.org/index.php/pacman)

To search for packages, the library can be browsed: [https://aur.archlinux.org/](https://aur.archlinux.org/)

For the most part I'm happy with the libraries that are offered. Coming from a Windows and Mac background, I still prefer NPM for managing packages so I installed NPM I followed this tutorial: [https://computingforgeeks.com/install-latet-nodejs-and-npm-on-centos-7-ubuntu-16-04-arch-linux-macos/](https://computingforgeeks.com/install-latet-nodejs-and-npm-on-centos-7-ubuntu-16-04-arch-linux-macos/)

To install NPM from command prompt, run this command: $ sudo pacman -S nodejs

Software I'm running currently:
* Visual Studio Code: [https://code.visualstudio.com/](https://code.visualstudio.com/)
* Left: [https://github.com/hundredrabbits/Left](https://github.com/hundredrabbits/Left)
* Firefox Nightly: [https://www.mozilla.org/en-US/firefox/channel/desktop/](https://www.mozilla.org/en-US/firefox/channel/desktop/)
* Hyper: [https://hyper.is/](https://hyper.is/)
* Android Studio: [https://developer.android.com/studio/](https://developer.android.com/studio/)


I've spent one day so far with Arch Linux and I'm pleased with the setup. Arch Linux brings me back to the DeviantArt Windows 2000 era when everything seemed customizable. Computing is downright fun with Arch Linux and I look forward to continuing to test its potential. 
