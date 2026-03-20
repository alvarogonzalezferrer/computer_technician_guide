# 🖥️ Computer Technician Guide

> *A practical guide to repair, optimize, and maintain your friends and family's computers.*
> You are "the" tech guy in the family, aren't you?

One of the hallmarks of our age is the decline of the do-it-yourselfer. Toilet not flushing? Hire a plumber. Lights on the blink? Hire an electrician. I'm a Computer Science graduate, so I get often called as "the" tech guy in the family. This guide exists so you (and they) never have to pay anyone for something you can do yourself.

---

## 🌐 Website with the guide

**[Check this guide as a website](https://alvarogonzalezferrer.github.io/computer_technician_guide/)**

If you find it useful, share it with other tech guys out there!

---

## 👤 Who am I?

Hi, I'm Alvaro - Software Developer and Computer Science graduate from Argentina, currently living in Costa Rica.

Check my portfolio: **[alvarogonzalezferrer.github.io](https://alvarogonzalezferrer.github.io/)**
I'm a freelancer, mainly expert in C++. You can hire me for your projects!

---

## 📋 Index

1. [For New Computers - Linux](#1-for-new-computers--linux)
2. [For New Computers - Windows](#2-for-new-computers--windows)
3. [Physical Tools - Opening & Maintaining PCs](#3-physical-tools---opening--maintaining-pcs)
4. [Rescue & Boot Tools](#4-rescue--boot-tools)
5. [Remote Desktop](#5-remote-desktop)
6. [Cleanup & Debloat](#6-cleanup--debloat)
7. [Recover Deleted Data](#7-recover-deleted-data)
8. [Backups](#8-backups)
9. [Virus & Malware](#9-virus--malware)
10. [Disk Health](#10-disk-health)
11. [Network Tools](#11-network-tools)
12. [Browsers](#12-browsers)
13. [Install / Update Software in Bulk](#13-install--update-software-in-bulk)
14. [File Managers & Search](#14-file-managers--search)
15. [Hardware Info & Diagnostics](#15-hardware-info--diagnostics)
16. [Password Managers](#16-password-managers)
17. [Office & Documents](#17-office--documents)
18. [PDF Tools](#18-pdf-tools)
19. [Media Players & Audio](#19-media-players--audio)
20. [Email Clients](#20-email-clients)
21. [Productivity & Notes](#21-productivity--notes)
22. [Graphics & Media](#22-graphics--media)
23. [Text Editors](#23-text-editors)
24. [Beyond Windows](#24-beyond-windows)
25. [Quick Reference - All Tools](#25-quick-reference--all-tools)

---

## 1. For New Computers - Linux

| Distro | Best for | Link |
|---|---|---|
| **Linux Mint** | New computers, Windows-like experience | [linuxmint.com](https://linuxmint.com/) |
| **Kubuntu** | New computers, KDE desktop | [kubuntu.org](https://kubuntu.org/) |
| **Lubuntu** | Old/slow computers | [lubuntu.me](https://lubuntu.me/) |
| **Xubuntu** | Old/slow computers, XFCE desktop | [xubuntu.org](https://xubuntu.org/) |

---

## 2. For New Computers - Windows

### Step 1 - Choose the right ISO

| Version | Description | Best for |
|---|---|---|
| **IoT LTSC** | Lightest version. Extremely clean, no bloatware. | Enthusiasts wanting maximum performance |
| **LTSC** | Long-term support. Security updates only. Clean by default. | Users wanting performance without fuss |
| **Consumer (Pro/Home)** | Standard version. More stable but full of preinstalled apps. | Users who need full Microsoft ecosystem |

> [!NOTE]
> For activation: **[MAS (Microsoft Activation Scripts)](https://github.com/massgravel/Microsoft-Activation-Scripts)**

Download clean ISOs: **[massgrave.dev](https://massgrave.dev)**

### Step 2 - Prepare the bootable USB

Use **[Rufus](https://rufus.ie)** - or **[Ventoy](https://www.ventoy.net/)** for a multiboot USB with multiple ISOs.

For **Windows 11**, enable in Rufus:
- [x] Remove requirement for 4+ GB RAM, Secure Boot, and TPM 2.0
- [x] Remove requirement for a Microsoft online account
- [x] Create a local account with a custom username
- [x] Disable data collection
- [x] Disable automatic BitLocker device encryption

### Step 3 - Clean GPU drivers

**Nvidia:** [NVCleanstall](https://www.techpowerup.com/nvcleanstall/) - select only Display Driver + Legacy Control Panel + Disable Telemetry + Disable MPO.

**AMD:** [AMD drivers](https://www.amd.com/en/support/download/drivers.html) + [Radeon Software Slimmer](https://github.com/GSDragoon/RadeonSoftwareSlimmer) - keep only Visual C++ Redistributable, disable all scheduled tasks.

### Step 4 - Install Windows

1. Boot from USB, follow normal installation.
2. Disconnect Ethernet/WiFi before first boot.
3. Windows 10 only - press `Shift + F10` when prompted for Microsoft account, then run `OOBE\BYPASSNRO`.
4. Install prepared GPU drivers. Reboot. Reconnect internet.

### Step 5 - Optimize the system

| Option | Method | Best for |
|---|---|---|
| **A** | Playbooks ([AtlasOS](https://atlasos.net) / [ReviOS](https://revi.cc)) via [AME Wizard](https://ameliorated.io) | Maximum performance |
| **B** | [ChrisTitus Script](https://christitus.com/win): `irm "https://christitus.com/win" \| iex` | Easy and effective |
| **A + B** | Both combined | Enthusiasts |

---

## 3. Physical Tools - Opening & Maintaining PCs

### Essential Hand Tools

| Tool | Why You Need It | Budget |
|---|---|---|
| **Precision screwdriver kit** (iFixit or 120+ bit generic) | Phillips #00 #0 #1, Torx T5/T6/T8, Pentalobe. Covers every laptop and desktop. | ~$15-25 |
| **ESD anti-static wrist strap** | One static discharge silently destroys RAM, SSDs, or GPUs. | ~$2-5 |
| **Plastic spudgers and pry tools** | Open laptop chassis without scratching or snapping clips. Never use metal. | ~$5-10 |
| **Plastic opening picks (6-pack)** | Slide around the laptop edge to release clips gradually. | ~$5 |
| **Anti-static tweezers** | Handle small connectors, SMD components, and screws in tight spots. | ~$5-10 |
| **Magnetic screw tray or mat** | Laptops have 20-40 screws of multiple sizes. Keep them organized. | ~$5-10 |

### Thermal Maintenance

| Tool | Why You Need It | Budget |
|---|---|---|
| **Thermal paste - Arctic MX-4 or MX-6** | Replace when reseating a CPU cooler or when laptop overheats. Safe home choice. | ~$7-10 |
| **Isopropyl alcohol 90-99%** | Remove old thermal paste, clean contacts. Must be high concentration. | ~$5-8 |
| **Electric air blower (rechargeable)** | Cleans dust from heatsinks and fans. Much better than canned air. | ~$15-25 |

### Electrical Diagnostics

| Tool | Why You Need It | Budget |
|---|---|---|
| **ATX PSU tester with LCD display** | Diagnoses a dead power supply in 30 seconds. Shows all voltage rails. No need to assemble the full PC. | ~$10-15 |
| **Digital multimeter (basic)** | Measure wall voltage, test batteries, check cable continuity. | ~$10-15 |
| **POST / debug card (PCIe)** | Shows hex code on LED display when PC won't POST. Identify failed component before Windows loads. | ~$5-10 |
| **RJ45 cable tester** | Verify ethernet cable continuity on all 8 pins. | ~$5-10 |

### Laptop-Specific

| Tool | Why You Need It | Budget |
|---|---|---|
| **USB to SATA adapter** | Connect removed HDD/SSD to another PC as external drive. Critical for data recovery. | ~$10-15 |
| **CMOS battery - CR2032 (pack of 5)** | When date resets on its own, this is usually the culprit. Keep a few in your drawer. | ~$3-5 |
| **Heat gun or hair dryer** | Soften adhesive on laptops that use glue instead of screws. | ~$15-30 |

> [!TIP]
> Starter kit under $60: screwdriver kit + ESD strap + thermal paste + IPA 99% + electric blower + PSU tester.

---

## 4. Rescue & Boot Tools

| Tool | Link | Notes |
|---|---|---|
| **Ventoy** | [ventoy.net](https://www.ventoy.net/) | Multiboot USB - multiple ISOs on one drive |
| **Hiren's BootCD PE** | [hirensbootcd.org](https://www.hirensbootcd.org/) | Bootable WinPE with dozens of repair tools |
| **Sergei Strelec's WinPE** | [sergeistrelec.ru](https://sergeistrelec.ru/) | Even larger WinPE collection than Hiren's |
| **Ultimate Boot CD** | [ultimatebootcd.com](https://www.ultimatebootcd.com/) | Hardware diagnostic tools bootable ISO |
| **SystemRescue** | [system-rescue.org](https://www.system-rescue.org/) | Linux-based rescue environment |
| **GParted Live** | [gparted.org](https://gparted.org/livecd.php) | Bootable partition editor |
| **Memtest86** | [memtest86.com](https://www.memtest86.com/) | RAM testing - run overnight |
| **Clonezilla** | [clonezilla.org](https://clonezilla.org/) | Disk cloning and imaging |

---

## 5. Remote Desktop

| Tool | Link | Notes |
|---|---|---|
| **RustDesk** | [rustdesk.com](https://rustdesk.com/) | Open source, self-hostable, privacy-first |
| **AnyDesk** | [anydesk.com](https://anydesk.com/) | Fast, lightweight, cross-platform |
| **TeamViewer** | [teamviewer.com](https://www.teamviewer.com/) | Classic choice, feature-rich |
| **UltraVNC** | [uvnc.com](https://uvnc.com/) | Open source, good for LAN |

---

## 6. Cleanup & Debloat

| Tool | Link | Purpose |
|---|---|---|
| **Bulk Crap Uninstaller** | [bcuninstaller.com](https://www.bcuninstaller.com/) | Mass uninstall apps cleanly |
| **BleachBit** | [bleachbit.org](https://www.bleachbit.org/) | Deep disk cleanup |
| **WizTree** | [diskanalyzer.com](https://diskanalyzer.com/) | Disk usage visualizer - much faster than WinDirStat |
| **WinDirStat** | [windirstat.net](https://windirstat.net/) | Disk usage visualizer - classic treemap |
| **Microsoft PowerToys** | [github.com/microsoft/PowerToys](https://github.com/microsoft/PowerToys) | Open source Microsoft toolkit with 20+ utilities |
| **Privatezilla** | [github.com/builtbybel/privatezilla](https://github.com/builtbybel/privatezilla) | Disable Windows telemetry and spyware |
| **DoNotSpy11** | [pxc-coding.com/donotspy11](https://pxc-coding.com/donotspy11/) | Disable Win10/11 telemetry |
| **LockHunter** | [lockhunter.com](https://lockhunter.com/) | Delete files that refuse to be deleted |
| **Czkawka** | [github.com/qarmin/czkawka](https://github.com/qarmin/czkawka) | Find and remove duplicate and unnecessary files |
| **Open-Shell** | [github.com/Open-Shell/Open-Shell-Menu](https://github.com/Open-Shell/Open-Shell-Menu) | Classic Start menu for Win 10/11 |

---

## 7. Recover Deleted Data

> [!CAUTION]
> I try to avoid this task. Have **BACKUPS** and educate your family about them.

| Tool | Link | Notes |
|---|---|---|
| **Recuva** | [ccleaner.com/recuva](https://www.ccleaner.com/recuva/) | Recover deleted files, easy UI |
| **TestDisk / PhotoRec** | [cgsecurity.org](https://www.cgsecurity.org/wiki/TestDisk) | Powerful open-source partition and file recovery |
| **Autopsy** | [sleuthkit.org/autopsy](https://www.sleuthkit.org/autopsy/) | Full digital forensics platform |

---

## 8. Backups

### The 3-2-1 Rule
1. **3** copies of your data
2. **2** different storage media types
3. **1** copy offsite (i.e., the cloud)

### Software

| Tool | Link | Notes |
|---|---|---|
| **Clonezilla** | [clonezilla.org](https://clonezilla.org/) | Disk cloning |
| **Rescuezilla** | [rescuezilla.com](https://rescuezilla.com/) | GUI-based Clonezilla |
| **7-Zip** | [7-zip.org](https://www.7-zip.org/) | Compression and archiving |
| **PeaZip** | [peazip.github.io](https://peazip.github.io/) | Open source 7-Zip alternative |
| **Duplicati** | [duplicati.com](https://www.duplicati.com/) | Free encrypted cloud backups |
| **FreeFileSync** | [freefilesync.org](https://freefilesync.org/) | Open-source file sync and backup |
| **Cryptomator** | [cryptomator.org](https://cryptomator.org/) | Encrypt files before uploading to cloud |
| **VeraCrypt** | [veracrypt.fr](https://www.veracrypt.fr/) | Full disk or container encryption |

---

## 9. Virus & Malware

My approach: full scan + immunization -> remove scanner -> leave Windows Defender.

| Tool | Link | Notes |
|---|---|---|
| **Windows Defender** | Built-in | Leave as the permanent AV |
| **Spybot Free** | [safer-networking.org](https://www.safer-networking.org/products/spybot-free-edition/) | Immunization feature - always run it |
| **Malwarebytes** | [malwarebytes.com](https://www.malwarebytes.com) | Great secondary scanner |
| **AdwCleaner** | [malwarebytes.com/adwcleaner](https://www.malwarebytes.com/adwcleaner/) | Adware and PUP remover |
| **RKill** | [bleepingcomputer.com/download/rkill](https://www.bleepingcomputer.com/download/rkill/) | Terminates malware processes before cleaning |
| **RogueKiller** | [adlice.com/roguekiller](https://www.adlice.com/roguekiller/) | Removes rootkits |

---

## 10. Disk Health

| Tool | Link | Notes |
|---|---|---|
| **CrystalDiskInfo** | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskinfo/) | S.M.A.R.T. health monitoring |
| **CrystalDiskMark** | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskmark/) | Disk speed benchmark |
| **HD Tune Free** | [hdtune.com](https://www.hdtune.com/) | Lightweight benchmark and health check |
| **HDDScan** | [hddscan.com](https://hddscan.com/) | Deep surface scan |
| **chkdsk** | Built-in | `chkdsk /f /r` in CMD as admin |

---

## 11. Network Tools

| Tool | Link | Notes |
|---|---|---|
| **Wireshark** | [wireshark.org](https://www.wireshark.org/) | Standard network protocol analyzer. Open source. |
| **Sniffnet** | [sniffnet.net](https://www.sniffnet.net/) | Simple visual network monitor. Shows which apps send data and where. |
| **Angry IP Scanner** | [angryip.org](https://angryip.org/) | Fast open-source IP/port scanner. See every device on your network. |
| **Advanced IP Scanner** | [advanced-ip-scanner.com](https://www.advanced-ip-scanner.com/) | Free, easy network scanner for home and small office. |
| **WinSCP** | [winscp.net](https://winscp.net/) | Free SFTP/FTP client. Transfer files to servers or NAS. |
| **PuTTY** | [putty.org](https://www.putty.org/) | Classic free SSH/Telnet client. |
| **Nmap** | [nmap.org](https://nmap.org/) | Open source network exploration and port scanning. |

---

## 12. Browsers

The browser is the most used application on any computer - and the most dangerous vector for tracking and malware. This list is ordered from **most recommended** to **least recommended**.

> [!IMPORTANT]
> **First thing to install on any browser:** [uBlock Origin](https://ublockorigin.com/).
> It blocks ads, trackers, and malware domains. It's not just about comfort - it's a security tool.

### Best - Open Source, Privacy-Respecting

| Browser | Notes | Link |
|---|---|---|
| **Firefox** | 100% open source. Not controlled by a surveillance company. Mozilla Foundation (non-profit). Excellent extension support. Install this on every machine you touch. | [mozilla.org/firefox](https://www.mozilla.org/firefox/) |
| **LibreWolf** | Firefox fork with all telemetry stripped and privacy hardened. uBlock Origin pre-installed. No Mozilla accounts, no Pocket. For advanced users - some sites may break. | [librewolf.net](https://librewolf.net/) |

### Good - Chromium-Based, Privacy-Conscious

| Browser | Notes | Link |
|---|---|---|
| **Brave** | Chromium with Google tracking removed. Built-in ad blocker, fingerprint randomization, optional Tor integration. The crypto/rewards system can be ignored entirely. | [brave.com](https://brave.com/) |
| **Ungoogled Chromium** | Chromium with all Google-specific code removed. No account integration, no telemetry. Installing extensions requires extra steps. | [ungoogled-software.github.io](https://ungoogled-software.github.io/) |

### Use With Caution - Surveillance by Design

| Browser | Notes | Link |
|---|---|---|
| **Google Chrome** | Google's most powerful data collection tool. Tracks browsing history, login activity, and behavior across all websites. Progressively limiting ad blocker effectiveness (Manifest V3). At minimum, install uBlock Origin. | [google.com/chrome](https://www.google.com/chrome/) |
| **Microsoft Edge** | Chromium-based with Microsoft telemetry and services on top. Syncs data to Microsoft, pushes Bing and Copilot constantly. Don't use as default browser. | Pre-installed on Windows |

### Essential Browser Extensions

| Extension | Link | Notes |
|---|---|---|
| **uBlock Origin** | [ublockorigin.com](https://ublockorigin.com/) | Blocks ads, trackers, malware domains. The single most important extension. Open source. No RAM impact. **MANDATORY.** |
| **SponsorBlock** | [sponsor.ajay.app](https://sponsor.ajay.app/) | Automatically skips sponsor segments, intros, and filler in YouTube videos. Crowd-sourced, open source. |
| **Privacy Badger** | [privacybadger.org](https://privacybadger.org/) | Learns to block invisible cross-site trackers. Made by the EFF. Complements uBlock Origin. |
| **Bitwarden** | [bitwarden.com](https://bitwarden.com/) | Browser extension for the Bitwarden password manager. Autofills passwords, warns about phishing sites. |
| **ClearURLs** | [clearurls.xyz](https://clearurls.xyz/) | Strips tracking parameters from URLs (UTM codes, fbclid, etc.) before you visit them. |
| **Dark Reader** | [darkreader.org](https://darkreader.org/) | Forces dark mode on every website. Open source. Very configurable. |
| **Return YouTube Dislike** | [returnyoutubedislike.com](https://returnyoutubedislike.com/) | Brings back the dislike count on YouTube videos. |

> [!NOTE]
> On Chrome and Edge, Google is phasing out the API that makes uBlock Origin fully effective (Manifest V3). On Firefox, it will continue to work at full power. One more reason to use Firefox.

---

## 13. Install / Update Software in Bulk

| Tool | Link | Notes |
|---|---|---|
| **Winget** | Built into Windows 11 | Official Microsoft package manager |
| **Ninite** | [ninite.com](https://ninite.com/) | Simple bulk installer, no bloat |
| **Chocolatey** | [chocolatey.org](https://chocolatey.org/) | CLI package manager |
| **Patch My PC** | [patchmypc.com](https://patchmypc.com/home-updater) | Auto-update installed software |
| **Snappy Driver Installer** | [sdi-tool.org](https://sdi-tool.org/) | Offline driver installer |

---

## 14. File Managers & Search

| Tool | Link | Notes |
|---|---|---|
| **Everything** | [voidtools.com](https://www.voidtools.com/en-us/) | Instant file search - far better than Windows Search |
| **Explorer++** | [explorerplusplus.com](https://explorerplusplus.com/) | Tabbed Windows Explorer replacement |
| **Total Commander** | [ghisler.com](https://www.ghisler.com/) | Dual-pane, very powerful |
| **qBittorrent** | [qbittorrent.org](https://www.qbittorrent.org/) | Download Linux ISOs via torrent. Open source, no ads. |

---

## 15. Hardware Info & Diagnostics

| Tool | Link | Purpose |
|---|---|---|
| **HWiNFO** | [hwinfo.com](https://www.hwinfo.com/) | Detailed hardware info and real-time sensors |
| **Libre Hardware Monitor** | [github.com/LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor) | Open source temperature and fan speed monitor |
| **CPU-Z** | [cpuid.com/softwares/cpu-z.html](https://www.cpuid.com/softwares/cpu-z.html) | CPU, RAM, and motherboard details |
| **GPU-Z** | [techpowerup.com/gpuz](https://www.techpowerup.com/gpuz/) | GPU details |
| **Sysinternals Suite** | [learn.microsoft.com/sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite) | Autoruns, Process Monitor, TCPView. Nothing hides from Autoruns. |
| **System Informer** | [systeminformer.com](https://systeminformer.com/) | Advanced Task Manager - shows hidden processes, per-process network activity |
| **NirSoft / NirLauncher** | [nirsoft.net](https://www.nirsoft.net/) | 250+ free portable utilities. Run from USB without installing. |
| **LatencyMon** | [resplendence.com/latencymon](https://www.resplendence.com/latencymon) | Diagnose real-time latency issues |
| **WhoCrashed** | [resplendence.com/whocrashed](https://www.resplendence.com/whocrashed) | Identifies drivers causing BSODs |
| **BATExpert / BatteryCare** | [batterycare.net](https://www.batterycare.net/) | Real battery health and cycle count on laptops |
| **FurMark** | [geeks3d.com/furmark](https://www.geeks3d.com/furmark/) | GPU stress test |
| **Prime95** | [mersenne.org/prime95](https://www.mersenne.org/prime95/) | CPU stress test |
| **Memtest86** | [memtest86.com](https://www.memtest86.com/) | RAM testing - run bootable overnight |

---

## 16. Password Managers

| Tool | Link | Notes |
|---|---|---|
| **Bitwarden** | [bitwarden.com](https://bitwarden.com/) | Open source, cloud-synced, free tier is excellent. Self-hostable with Vaultwarden. |
| **KeePassXC** | [keepassxc.org](https://keepassxc.org/) | Local only, no cloud, encrypted database file. |

---

## 17. Office & Documents

| Tool | Link | Notes |
|---|---|---|
| **LibreOffice** | [libreoffice.org](https://www.libreoffice.org/) | Full suite - Writer, Calc, Impress. The free answer to Microsoft Office. |
| **OnlyOffice Desktop** | [onlyoffice.com/desktop.aspx](https://www.onlyoffice.com/desktop.aspx) | Better Microsoft Office compatibility than LibreOffice. |

---

## 18. PDF Tools

| Tool | Link | Notes |
|---|---|---|
| **Sumatra PDF** | [sumatrapdfreader.org](https://www.sumatrapdfreader.org/) | Ultralight reader, 2MB, zero bloat. Replaces Adobe Reader completely. |
| **PDF24** | [pdf24.org](https://www.pdf24.org/) | Merge, split, compress, convert PDFs. Files stay local. |

---

## 19. Media Players & Audio

| Tool | Link | Notes |
|---|---|---|
| **VLC** | [videolan.org/vlc](https://www.videolan.org/vlc/) | Plays everything. Always install this first. |
| **foobar2000** | [foobar2000.org](https://www.foobar2000.org/) | Lightweight, extensible music player. Zero bloat. |
| **MPC-HC** | [github.com/clsid2/mpc-hc](https://github.com/clsid2/mpc-hc) | Media Player Classic - minimal, fast, open source. |
| **Audacity** | [audacityteam.org](https://www.audacityteam.org/) | Open source audio editor and recorder. |

---

## 20. Email Clients

| Tool | Link | Notes |
|---|---|---|
| **Thunderbird** | [thunderbird.net](https://www.thunderbird.net/) | Open source, by Mozilla. Supports Gmail, Outlook, any IMAP/SMTP. |
| **Mailspring** | [getmailspring.com](https://getmailspring.com/) | Modern UI, free, open source. |

---

## 21. Productivity & Notes

| Tool | Link | Notes |
|---|---|---|
| **Obsidian** | [obsidian.md](https://obsidian.md/) | Local Markdown notes, free for personal use. Plain text files - yours forever. |
| **Joplin** | [joplinapp.org](https://joplinapp.org/) | Open source notes with sync. Good Evernote replacement. |
| **ShareX** | [getsharex.com](https://getsharex.com/) | Screenshots, recording, OCR, annotations. Open source. |

---

## 22. Graphics & Media

### Video Editing
[DaVinci Resolve](https://www.blackmagicdesign.com/products/davinciresolve/) - [OpenShot](https://www.openshot.org/) - [Kdenlive](https://kdenlive.org/) - [OBS Studio](https://obsproject.com/)

### Image Editing
[GIMP](https://www.gimp.org/) - [Paint.NET](https://www.getpaint.net/) - [Inkscape](https://inkscape.org/) - [Krita](https://krita.org/) - [IrfanView](https://www.irfanview.com/)

### 3D
[Blender](https://www.blender.org/) - [Wings 3D](http://www.wings3d.com/)

---

## 23. Text Editors

[VS Code](https://code.visualstudio.com/) - [Notepad++](https://notepad-plus-plus.org/) - [CudaText](https://cudatext.github.io/) - [Sublime Text](https://www.sublimetext.com/)

---

## 24. Beyond Windows

- **AutoHotkey** - [autohotkey.com](https://www.autohotkey.com/) - Automation and keyboard shortcuts
- **VirtualBox** - [virtualbox.org](https://www.virtualbox.org/) - Virtual machines
- **QEMU** - [qemu.org](https://www.qemu.org/) - Virtual machines, open source
- **DOSBox** - [dosbox.com](https://www.dosbox.com/) - Retro DOS gaming
- **Hackintosh** - [hackintosh.com](https://hackintosh.com/) - Run macOS on unsupported hardware

---

## 25. Quick Reference - All Tools

| Tool | Link |
|---|---|
| MassGrave (ISOs) | [massgrave.dev](https://massgrave.dev) |
| MAS (Activation) | [github.com/massgravel/MAS](https://github.com/massgravel/Microsoft-Activation-Scripts) |
| Rufus | [rufus.ie](https://rufus.ie) |
| Ventoy | [ventoy.net](https://www.ventoy.net/) |
| Firefox | [mozilla.org/firefox](https://www.mozilla.org/firefox/) |
| LibreWolf | [librewolf.net](https://librewolf.net/) |
| Brave | [brave.com](https://brave.com/) |
| uBlock Origin | [ublockorigin.com](https://ublockorigin.com/) |
| SponsorBlock | [sponsor.ajay.app](https://sponsor.ajay.app/) |
| Privacy Badger | [privacybadger.org](https://privacybadger.org/) |
| Bitwarden | [bitwarden.com](https://bitwarden.com/) |
| KeePassXC | [keepassxc.org](https://keepassxc.org/) |
| VLC | [videolan.org/vlc](https://www.videolan.org/vlc/) |
| LibreOffice | [libreoffice.org](https://www.libreoffice.org/) |
| Sumatra PDF | [sumatrapdfreader.org](https://www.sumatrapdfreader.org/) |
| Thunderbird | [thunderbird.net](https://www.thunderbird.net/) |
| Obsidian | [obsidian.md](https://obsidian.md/) |
| ShareX | [getsharex.com](https://getsharex.com/) |
| NirSoft / NirLauncher | [nirsoft.net](https://www.nirsoft.net/) |
| Sysinternals Suite | [microsoft.com/sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite) |
| Wireshark | [wireshark.org](https://www.wireshark.org/) |
| Sniffnet | [sniffnet.net](https://www.sniffnet.net/) |
| Angry IP Scanner | [angryip.org](https://angryip.org/) |
| Everything (search) | [voidtools.com](https://www.voidtools.com/) |
| HWiNFO | [hwinfo.com](https://www.hwinfo.com/) |
| RustDesk | [rustdesk.com](https://rustdesk.com/) |
| Hiren's BootCD PE | [hirensbootcd.org](https://www.hirensbootcd.org/) |
| OBS Studio | [obsproject.com](https://obsproject.com/) |
| GIMP | [gimp.org](https://www.gimp.org/) |
| Blender | [blender.org](https://www.blender.org/) |
| VS Code | [code.visualstudio.com](https://code.visualstudio.com/) |
| VirtualBox | [virtualbox.org](https://www.virtualbox.org/) |
| Malwarebytes | [malwarebytes.com](https://www.malwarebytes.com) |

---

## 📌 Version

`v0.4.0` - March 2026 - Added: Browsers section (Firefox/LibreWolf/Brave ranked, Chrome/Edge caveats), Browser extensions (uBlock Origin, SponsorBlock, Privacy Badger, ClearURLs, Dark Reader), improved readability across the HTML site, clean commented HTML/CSS code

---

<div align="center">

*This list is NOT exhaustive, nor does it contain "the TRUE word of GOD himself."*
*It's just what* works for me™

If you know a better way - send a pull request and improve it!

**For now, this is the way.**

</div>
