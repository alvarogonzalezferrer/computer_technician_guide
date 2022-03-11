# Computer technician guide

 A *computer technician guide* to repair your friends and family computer. You are "the" tech guy in the family, don't you?

 One of the hallmarks of our age is the decline of the do-it-yourselfer in favor of the hire-an-expert-to-do-it-insteader. Toilet not flushing? Hire a plumber. Porch falling down? Hire a carpenter. Lights on the blink? Hire an electrician.

 You could argue, as many people have done, that a return to a DIY ethos would be good for society and good for the soul. I like to DIY. Also, I'm a Computer Science graduate, so I get often called as "the" tech guy in family and circle of friends.


## Version

Revision v0.0.4 - March 2022

## Motivation

Everybody that has worked in the Computer Science field knows it. You are "the" tech guy in the family or circle of friends.

You get the late 4 am call of a desperate aunt that needs to finish work and the computer simply wont work, or a cousin that has a new computer without operating system.

Doesn't matter if you work for NASA, or if you have twenty years working in C++, for them your work is "repair computers". They will get mad if you don't repair their computer. Even if you don't have a clue how to do it since you're into algorithms and stuff far away from the mundane software.

So well, here comes this little guide, mainly done for myself, the quick and dirty guide to fix someone's else computer at 4 am a Thursday...

This list is NOT extensive, nor has "the TRUE word of GOD himself" into it. Is just a random guide of the things that *works for me*™ .

I try to use open source software, avoid bloatware, crapware, and paid software at all costs.

If you know a better way, please let me know, or better send a pull request and improve it!

For now, *this is the way*...

# Who am I?

Hi, Im Alvaro, Software developer and Computer Science graduate from Argentina.

Currently living at Costa Rica.

Check my portfolio for more info:

https://alvarogonzalezferrer.github.io/

There you can see my portfolio, I'm a freelancer, mainly expert in C++, you can hire me for your projects!

# Donate please

TODO - please donate or use my refer codes

# For new computers

# Linux

Just get Linux Mint or Kubuntu if you have a new computer.  

https://linuxmint.com/

https://kubuntu.org/

Lubuntu or Xubuntu if you have a old slow computer.

https://lubuntu.me/

https://xubuntu.org/

These Linux distros come ready out of the box, saving you all the trouble of Windows (but you do have some compatibility issues).

Enjoy

# Windows

For new computers or *recently formated*.

Install the operating system, drivers and software (see automated installers below, i.e Snappy, Patch My Pc or Ninite).

1. Get Windows 10 :
- https://www.microsoft.com/en-us/software-download/windows10
or
- https://tb.rg-adguard.net/public.php

2. Activate it. Purchase keys, or download and run MAS (Microsoft-Activation-Scripts) to activate.

- https://github.com/massgravel/Microsoft-Activation-Scripts

3. Install drivers, i.e with Snappy

4. Disable telemetry, cortana, ms store, xbox bullshit, and all the crap that win10 has... i.e with Privatezilla

5. Set it up to work fast, put classic start, disable all visual effects.

6. Install user software as needed. i.e with Ninite or Chocolatey

## Classic start menu

The Windows 10 start menu sucks, is slow, I prefer Open Shell

* Classic style Start Menu for Windows 7, 8, 8.1, 10: https://open-shell.github.io/Open-Shell-Menu/

## Drivers

* Snappy auto driver updater - installar: https://sdi-tool.org/

# Software for Windows  

## Remote Desktop

Adding that they always call around 2 am to 4 am, the family member in trouble is usually at the other side of the globe, so a remote desktop software is a must.

* Any Desk

* Team Viewer

* UltraVNC

Now you are into their computer... time to work, mostly automated so I don't lose my valuable time. I usually have a script with a pack with the software I'm going to use. Download the pack, run it and be done.

## Cleanup

* Bulk Crap Uninstaller

* Bleach Bit

* Privatezilla - disable windows telemetry and general spyware from micro$oft... - https://www.builtbybel.com/ms-apps/privatezilla

* DoNotSpy10 - disable Win10 telemetry and spyware - https://pxc-coding.com/donotspy10/

* Lock Hunter - https://lockhunter.com/ -- To delete those files that can't be deleted.

* Czkawka  - https://qarmin.github.io/czkawka/ -- remove unnecessary files from your computer

* Dupe Guru - https://dupeguru.voltaicideas.net/ -- find duplicate files

* Windirstat - https://windirstat.net/ --  disk usage statistics viewer and cleanup tool

* Defraggler -- defrag disk , old school, I usually don't do it.

Obsolete:
* FSLint - https://www.pixelbeat.org/fslint/ -- find and clean various forms of lint on a filesystem , duplicate files, etc

## Recover deleted data

I try to avoid this task, please have **BACKUPS**!

**Educate your family and friends on the importance of having BACKUPS**

* Autopsy - http://www.sleuthkit.org/autopsy/index.php -- digital forensics platform

* Recuva -- recover deleted files

Alternatives:

https://alternativeto.net/software/recuva/

## Backups

Golden Rules for data backup:

An easy-to-remember acronym for a common approach to keeping your data safe is 3-2-1 backup rule in almost any failure scenario. The rule is:

1. Keeps at least three copies of your data

2. Stores two backup copies on different storage media

3. With one of them located offsite. i.e "the cloud"

### Software for backups

* 7-Zip -- Pretty good, not only for backup, replaces WinRar, Winzip, etc : https://www.7-zip.org/

## Cloud Storage

TODO - I prefer pCloud

## Virus and malware

I usually install a scanner, do the scan, then remove it and leave Windows Defender, since the hardware of my circle of friends is usually very modest and slow, so antivirus usually make it crawl.

* Avira Free - https://www.avira.com/en/free-antivirus-windows

* Spybot Free Edition - https://www.safer-networking.org/products/spybot-free-edition/
  * Has a cool "inmunization" feature. Use it.

* Windows Defender - https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10

I leave this after the full scan, inmunization, etc, removing all the others.

### Other anti virus tools

I almost never use these, but good to know them

* MBAM - https://malwarebytes.com

* Rogue Killer - https://www.adlice.com/roguekiller/

* ADW Cleaer - https://www.malwarebytes.com/adwcleaner/

* OS Armor - https://www.osarmor.com/

* RKill - https://www.bleepingcomputer.com/download/rkill/

* Panda Autorun Vaccine - https://www.pandasecurity.com/en/mediacenter/products/panda-usb-and-autorun-vaccine/

* Hijack This - obsolete? I think there is a fork that still works

* ClamAV - open source - https://www.clamav.net/

## Check disk health

* chkdsk

* https://hddscan.com/

* https://crystalmark.info/en/software/crystaldiskinfo/

etc - TODO

## Install / update user software

Install or update software in bulk. Save time and effort.

* Patch My PC - https://patchmypc.com/home-updater

* Ninite - https://ninite.com/

* Chocolatey - https://chocolatey.org/

* Snappy - drivers - https://sdi-tool.org/

* Just Install - https://github.com/just-install/just-install

Within Chrome or Firefox: run **uBlock Origin** is a must.

## File manager

* Total Commander - https://www.ghisler.com/

* Far Manager - https://www.farmanager.com/

* MultiCommander - http://multicommander.com/

* Everything - file search local, way better than cortana: https://www.voidtools.com/en-us/

# Hardware check

* Who Crashed - https://www.resplendence.com/whocrashed - reveals the drivers responsible for crashing your computer

Getting info about the hardware

* Speccy - https://www.ccleaner.com/speccy

* HWiNFO - https://www.hwinfo.com/

## Testing

TO-DO

## Repairing

TO-DO

## Replacing

TO-DO

## Reusing

TO-DO

# Some other useful tools 

Some apps that are very useful 

## Video editing 

* Davinci Resolve - https://www.blackmagicdesign.com/products/davinciresolve/ 
* Openshot
* Pitivi
* Cinelerra

## Shortcuts 

* Fatkeys - https://www.fastkeysautomation.com/

## Screen capture and broadcast 

* OBS studio - https://obsproject.com/es
* ScreenPresso - https://www.screenpresso.com/

## Graphics

* Paint NET
* GIMP
* Inkscape 
* Irfanview 
* ASE Sprite Editor
* Wings 3D
* Blender


# Beyond Windows

## Linux

* Linux Mint - https://linuxmint.com/

## DosBox

Retro fun, and games with no shitty loot boxes or milking you for money with DLCs... the golden age of computing...

* https://www.dosbox.com/

## Virtual Computers

* Virtual Box - https://www.virtualbox.org/

* QEMU - https://www.qemu.org/

## Hackintosh

Hackintosh.com links to everything you need to build a Hackintosh and get macOS Monterey (macOS 12) as well as many earlier versions of Mac OS X running on an unsupported computer

* https://hackintosh.com/
