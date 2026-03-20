# 🖥️ Computer Technician Guide

> *A practical guide to repair, optimize, and maintain your friends and family's computers.*  
> You are "the" tech guy in the family, aren't you?

One of the hallmarks of our age is the decline of the do-it-yourselfer. Toilet not flushing? Hire a plumber. Lights on the blink? Hire an electrician. I'm a Computer Science graduate, so I get often called as "the" tech guy in the family. This guide exists so you (and they) never have to pay anyone for something you can do yourself.

---

## 👤 Who am I?

Hi, I'm Alvaro — Software Developer and Computer Science graduate from Argentina, currently living in Costa Rica.

Check my portfolio: **[alvarogonzalezferrer.github.io](https://alvarogonzalezferrer.github.io/)**  
I'm a freelancer, mainly expert in C++. You can hire me for your projects!

---

## 📋 Index

1. [For New Computers — Linux](#1-for-new-computers--linux)
2. [For New Computers — Windows](#2-for-new-computers--windows)
   - [Step 1 — Choose the right ISO](#step-1--choose-the-right-iso)
   - [Step 2 — Prepare the bootable USB](#step-2--prepare-the-bootable-usb)
   - [Step 3 — Clean GPU drivers](#step-3--clean-gpu-drivers)
   - [Step 4 — Install Windows](#step-4--install-windows)
   - [Step 5 — Optimize the system](#step-5--optimize-the-system)
3. [Rescue & Boot Tools](#3-rescue--boot-tools)
4. [Remote Desktop](#4-remote-desktop)
5. [Cleanup & Debloat](#5-cleanup--debloat)
6. [Recover Deleted Data](#6-recover-deleted-data)
7. [Backups](#7-backups)
8. [Virus & Malware](#8-virus--malware)
9. [Disk Health](#9-disk-health)
10. [Install / Update Software in Bulk](#10-install--update-software-in-bulk)
11. [File Managers & Search](#11-file-managers--search)
12. [Hardware Info & Diagnostics](#12-hardware-info--diagnostics)
13. [Password Managers](#13-password-managers)
14. [Office & Documents](#14-office--documents)
15. [PDF Tools](#15-pdf-tools)
16. [Media Players & Audio](#16-media-players--audio)
17. [Email Clients](#17-email-clients)
18. [Productivity & Notes](#18-productivity--notes)
19. [Graphics & Media](#19-graphics--media)
20. [Text Editors](#20-text-editors)
21. [Beyond Windows](#21-beyond-windows)
22. [Quick Reference — All Tools](#22-quick-reference--all-tools)

---

## 1. For New Computers — Linux

If you want to avoid Windows headaches entirely:

| Distro | Best for | Link |
|---|---|---|
| **Linux Mint** | New computers, Windows-like experience | [linuxmint.com](https://linuxmint.com/) |
| **Kubuntu** | New computers, KDE desktop | [kubuntu.org](https://kubuntu.org/) |
| **Lubuntu** | Old/slow computers | [lubuntu.me](https://lubuntu.me/) |
| **Xubuntu** | Old/slow computers, XFCE desktop | [xubuntu.org](https://xubuntu.org/) |

These come ready out of the box — though you do have some software compatibility trade-offs.

---

## 2. For New Computers — Windows

---

### Step 1 — Choose the right ISO

Download a **clean ISO** directly. Don't modify or debloat the ISO itself — it's a waste of time.

| Version | Description | Best for |
|---|---|---|
| **IoT LTSC** | Lightest version of all. Extremely clean, no bloatware. | Enthusiasts wanting maximum performance |
| **LTSC** | Long-term support. Security updates only. Clean by default. | Users wanting performance without fuss |
| **Consumer (Pro/Home)** | Standard version. More stable but full of preinstalled apps. | Users who need full Microsoft ecosystem |

> [!WARNING]
> **Windows 10** no longer receives feature updates. LTSC versions still get security patches. If you're comfortable managing your own security, **Windows 10 LTSC** is an excellent lightweight option.

> [!NOTE]
> For activation, download and run **[MAS (Microsoft Activation Scripts)](https://github.com/massgravel/Microsoft-Activation-Scripts)**.

📥 Download clean ISOs from **[massgrave.dev](https://massgrave.dev)**

---

### Step 2 — Prepare the bootable USB

Use **[Rufus](https://rufus.ie)** to write the ISO to your USB drive.

> [!TIP]
> Use **[Ventoy](https://www.ventoy.net/)** if you want a multiboot USB — load multiple ISOs on a single drive and pick which one to boot. Essential for any technician's toolkit.

If installing **Windows 11**, Rufus offers critical bypass options. Check all of these:

- [x] Remove requirement for 4+ GB RAM, Secure Boot, and TPM 2.0
- [x] Remove requirement for a Microsoft online account
- [x] Create a local account with a custom username
- [x] Disable data collection (skip privacy questions)
- [x] Disable automatic BitLocker device encryption

---

### Step 3 — Clean GPU drivers

**Before installing Windows**, prepare a slim driver package on the same USB.

#### 🟢 Nvidia GPU — NVCleanstall

1. Download **[NVCleanstall](https://www.techpowerup.com/nvcleanstall/)**
2. Components to install:
   - [x] Display Driver *(required)*
   - [x] Legacy Control Panel
   - [ ] HD Audio via HDMI *(only if you use audio through monitor/TV)*
3. Tweaks tab:
   - [x] Disable Installer Telemetry & Advertising
   - [x] Perform a Clean Installation
   - [x] Disable Multiplane Overlay (MPO)
4. Click **Build Package** → copy the `.exe` to your USB.

#### 🔴 AMD GPU — Radeon Software Slimmer

1. Download the **WHQL** driver from [AMD's official site](https://www.amd.com/en/support/download/drivers.html).
2. Download **[Radeon Software Slimmer](https://github.com/GSDragoon/RadeonSoftwareSlimmer)**
3. In `Packages`: keep only Microsoft Visual C++ Redistributable. Uncheck all HDMI audio if not needed.
4. In `Scheduled Tasks`: disable all AMD auto-update tasks.
5. In `Display Driver Components`: keep only AMD Crash Defender and AMD-Windows Support Components.
6. Click **Modify Installer** → copy output folder to USB.

---

### Step 4 — Install Windows

1. Boot from USB and follow the normal installation.
2. **When Windows is about to start for the first time** — disconnect Ethernet/WiFi.
3. **Windows 10 only** — when prompted for a Microsoft account, press `Shift + F10`:

```
OOBE\BYPASSNRO
```

4. Inside Windows, install your prepared GPU drivers. Reboot.
5. Reconnect to the internet.

---

### Step 5 — Optimize the system

| Option | Method | Aggressiveness | Best for |
|---|---|---|---|
| **A** | Playbooks (AtlasOS / ReviOS) | 🔴 High | Maximum performance |
| **B** | ChrisTitus Script | 🟡 Medium | Easy and effective |
| **A + B** | Both combined | 🔴🔴 Maximum | Enthusiasts |

#### Option A — Playbooks (AtlasOS / ReviOS)

| | **AtlasOS** | **ReviOS** |
|---|---|---|
| **Focus** | Stability | Maximum performance |
| **Windows 10** | ❌ Not supported | ✅ Supported |
| **Windows 11** | ✅ Supported | ✅ Supported |
| **Download** | [atlasos.net](https://atlasos.net) | [revi.cc](https://revi.cc) |

1. Download the Playbook and **[AME Wizard](https://ameliorated.io)**
2. Open AME Wizard, drag the Playbook in, follow prompts.
3. PC reboots automatically. ✅

#### Option B — ChrisTitus Script

```powershell
irm "https://christitus.com/win" | iex
```

**✅ Essential Tweaks** *(enable all)*

- [x] Create Restore Point
- [x] Delete Temporary Files
- [x] Disable Activity History
- [x] Disable ConsumerFeatures
- [x] Disable Explorer Automatic Folder Discovery
- [x] Disable Hibernation
- [x] Disable Location Tracking
- [x] Disable PowerShell 7 Telemetry
- [x] Disable Telemetry
- [x] Disable Windows Platform Binary Table (WPBT)
- [x] Enable End Task With Right Click
- [x] Remove Widgets
- [x] Run Disk Cleanup
- [x] Set Services to Manual

**⚠️ Advanced Tweaks**

- [x] Disable Microsoft Copilot
- [x] Remove Microsoft Edge
- [x] Remove OneDrive
- [x] Remove Xbox & Gaming Components
- [ ] Remove ALL MS Store Apps — ⛔ Not recommended

**🔧 Preferences**

- [x] Dark Theme for Windows
- [x] Disable Multiplane Overlay
- [x] Modern Standby Fix
- [x] Show File Extensions

```
→ Add and Activate Ultimate Performance Profile
```

> [!IMPORTANT]
> If you removed Edge and need a browser: the **first tab** of the script lets you install Chrome, Firefox, Brave, etc.

Reboot when done. ✅

#### Bonus — Overclock & Undervolt

| Technique | What it does | Result |
|---|---|---|
| **Overclock** | Increases CPU/GPU/RAM frequency above factory spec | More raw performance |
| **Undervolt** | Reduces voltage while maintaining performance | Less heat, less power, more stability |

> [!NOTE]
> One-on-one only — every component varies. No universal recipe.

---

## 3. Rescue & Boot Tools

Essential when Windows won't boot or the system is unrecoverable from inside.

| Tool | Link | Notes |
|---|---|---|
| **Ventoy** | [ventoy.net](https://www.ventoy.net/) | Multiboot USB — put multiple ISOs on one drive |
| **Hiren's BootCD PE** | [hirensbootcd.org](https://www.hirensbootcd.org/) | Swiss-army knife for rescue — bootable WinPE with dozens of tools |
| **SystemRescue** | [system-rescue.org](https://www.system-rescue.org/) | Linux-based rescue environment |
| **Clonezilla** | [clonezilla.org](https://clonezilla.org/) | Disk cloning & imaging |
| **Rescuezilla** | [rescuezilla.com](https://rescuezilla.com/) | GUI-based Clonezilla alternative |
| **GParted Live** | [gparted.org](https://gparted.org/livecd.php) | Partition editor, bootable |
| **Memtest86** | [memtest86.com](https://www.memtest86.com/) | RAM testing — run overnight |

> [!TIP]
> Load all of these onto a single Ventoy USB. That one drive replaces a whole bag of USBs.

---

## 4. Remote Desktop

Because the family member in trouble is always on the other side of the globe at 3am.

| Tool | Link | Notes |
|---|---|---|
| **RustDesk** | [rustdesk.com](https://rustdesk.com/) | Open source, self-hostable, privacy-first |
| **AnyDesk** | [anydesk.com](https://anydesk.com/) | Fast, lightweight, cross-platform |
| **TeamViewer** | [teamviewer.com](https://www.teamviewer.com/) | Classic choice, feature-rich |
| **UltraVNC** | [uvnc.com](https://uvnc.com/) | Open source, good for LAN |

---

## 5. Cleanup & Debloat

| Tool | Link | Purpose |
|---|---|---|
| **Bulk Crap Uninstaller** | [bcuninstaller.com](https://www.bcuninstaller.com/) | Mass uninstall apps cleanly |
| **BleachBit** | [bleachbit.org](https://www.bleachbit.org/) | Deep disk cleanup |
| **Privatezilla** | [github.com/builtbybel/privatezilla](https://github.com/builtbybel/privatezilla) | Disable Windows telemetry & spyware |
| **DoNotSpy11** | [pxc-coding.com/donotspy11](https://pxc-coding.com/donotspy11/) | Disable Win10/11 telemetry |
| **LockHunter** | [lockhunter.com](https://lockhunter.com/) | Delete files that refuse to be deleted |
| **Czkawka** | [github.com/qarmin/czkawka](https://github.com/qarmin/czkawka) | Remove unnecessary & duplicate files |
| **dupeGuru** | [dupeguru.voltaicideas.net](https://dupeguru.voltaicideas.net/) | Find duplicate files |
| **WinDirStat** | [windirstat.net](https://windirstat.net/) | Disk usage visualizer & cleanup |
| **Defraggler** | [ccleaner.com/defraggler](https://www.ccleaner.com/defraggler/) | Disk defrag *(HDDs only — never defrag an SSD)* |
| **Open-Shell** | [github.com/Open-Shell/Open-Shell-Menu](https://github.com/Open-Shell/Open-Shell-Menu) | Classic Start menu for Win 10/11 |

---

## 6. Recover Deleted Data

> [!CAUTION]
> I try to avoid this task. Have **BACKUPS** and educate your family about them.

| Tool | Link | Notes |
|---|---|---|
| **Recuva** | [ccleaner.com/recuva](https://www.ccleaner.com/recuva/) | Recover deleted files, easy UI |
| **TestDisk / PhotoRec** | [cgsecurity.org](https://www.cgsecurity.org/wiki/TestDisk) | Powerful open-source partition & file recovery |
| **Autopsy** | [sleuthkit.org/autopsy](https://www.sleuthkit.org/autopsy/) | Full digital forensics platform |

---

## 7. Backups

### The 3-2-1 Rule

1. **3** copies of your data
2. **2** different storage media types
3. **1** copy offsite (i.e., the cloud)

### Disk Cloning

| Tool | Link |
|---|---|
| **Clonezilla** | [clonezilla.org](https://clonezilla.org/) |
| **Rescuezilla** | [rescuezilla.com](https://rescuezilla.com/) |

### Backup Software

| Tool | Link | Notes |
|---|---|---|
| **7-Zip** | [7-zip.org](https://www.7-zip.org/) | Compression & archiving — replaces WinRAR/WinZip |
| **PeaZip** | [peazip.github.io](https://peazip.github.io/) | Open source 7-Zip alternative with modern GUI |
| **Duplicati** | [duplicati.com](https://www.duplicati.com/) | Free encrypted cloud backups |
| **FreeFileSync** | [freefilesync.org](https://freefilesync.org/) | Open-source file sync & backup |

### Cloud Storage

| Service | Link |
|---|---|
| **pCloud** | [pcloud.com](https://www.pcloud.com/) |
| **Google Drive** | [drive.google.com](https://drive.google.com/) |
| **Dropbox** | [dropbox.com](https://www.dropbox.com/) |
| **OneDrive** | [onedrive.live.com](https://onedrive.live.com/) |

### Encrypt Cloud Storage

| Tool | Link |
|---|---|
| **Cryptomator** | [cryptomator.org](https://cryptomator.org/) |
| **VeraCrypt** | [veracrypt.fr](https://www.veracrypt.fr/) |

---

## 8. Virus & Malware

My approach: full scan + immunization → remove scanner → leave Windows Defender. Most family hardware is modest and full-time AV tends to crawl it.

### Scanners

| Tool | Link | Notes |
|---|---|---|
| **Windows Defender** | Built-in | Leave as the permanent AV |
| **Avira Free** | [avira.com](https://www.avira.com/en/free-antivirus-windows) | Good free one-time scanner |
| **Spybot Free** | [safer-networking.org](https://www.safer-networking.org/products/spybot-free-edition/) | Has a great "immunization" feature — always use it |
| **Malwarebytes (MBAM)** | [malwarebytes.com](https://www.malwarebytes.com) | Great secondary scanner |
| **ClamAV** | [clamav.net](https://www.clamav.net/) | Open source |

### Specialized Tools

| Tool | Link |
|---|---|
| **RogueKiller** | [adlice.com/roguekiller](https://www.adlice.com/roguekiller/) |
| **AdwCleaner** | [malwarebytes.com/adwcleaner](https://www.malwarebytes.com/adwcleaner/) |
| **RKill** | [bleepingcomputer.com/download/rkill](https://www.bleepingcomputer.com/download/rkill/) |
| **Panda USB Vaccine** | [pandasecurity.com](https://www.pandasecurity.com/en/mediacenter/products/panda-usb-and-autorun-vaccine/) |
| **OSArmor** | [osarmor.com](https://www.osarmor.com/) |

> [!TIP]
> Always install **[uBlock Origin](https://ublockorigin.com/)** in Chrome or Firefox. No exceptions.

---

## 9. Disk Health

| Tool | Link | Notes |
|---|---|---|
| **CrystalDiskInfo** | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskinfo/) | S.M.A.R.T. health monitoring |
| **HDDScan** | [hddscan.com](https://hddscan.com/) | Deep scan for HDD/SSD/NVMe |
| **chkdsk** | Built-in | `chkdsk /f /r` in CMD as admin |

---

## 10. Install / Update Software in Bulk

| Tool | Link | Notes |
|---|---|---|
| **Winget** | Built into Windows 11 | Official Microsoft package manager |
| **Ninite** | [ninite.com](https://ninite.com/) | Simple bulk installer, no bloat |
| **Chocolatey** | [chocolatey.org](https://chocolatey.org/) | CLI package manager |
| **Patch My PC** | [patchmypc.com](https://patchmypc.com/home-updater) | Auto-update installed software |
| **Snappy Driver Installer** | [sdi-tool.org](https://sdi-tool.org/) | Offline driver installer |
| **Just Install** | [github.com/just-install/just-install](https://github.com/just-install/just-install) | Minimal CLI installer |

---

## 11. File Managers & Search

| Tool | Link | Notes |
|---|---|---|
| **Everything** | [voidtools.com](https://www.voidtools.com/en-us/) | Instant file search — far better than Windows Search |
| **Explorer++** | [explorerplusplus.com](https://explorerplusplus.com/) | Tabbed Windows Explorer replacement |
| **Total Commander** | [ghisler.com](https://www.ghisler.com/) | Dual-pane, very powerful |
| **Far Manager** | [farmanager.com](https://www.farmanager.com/) | Console-style dual-pane |
| **MultiCommander** | [multicommander.com](http://multicommander.com/) | Feature-rich dual-pane |
| **Meld** | [meldmerge.org](https://meldmerge.org/) | Merge/diff files, dirs, and repos |
| **qBittorrent** | [qbittorrent.org](https://www.qbittorrent.org/) | Download Linux ISOs and open-source software via torrent — open source, no ads |

---

## 12. Hardware Info & Diagnostics

| Tool | Link | Purpose |
|---|---|---|
| **HWiNFO** | [hwinfo.com](https://www.hwinfo.com/) | Detailed hardware info & real-time sensors |
| **Speccy** | [ccleaner.com/speccy](https://www.ccleaner.com/speccy) | Quick hardware overview |
| **CPU-Z** | [cpuid.com/softwares/cpu-z.html](https://www.cpuid.com/softwares/cpu-z.html) | CPU, RAM, motherboard details |
| **GPU-Z** | [techpowerup.com/gpuz](https://www.techpowerup.com/gpuz/) | GPU details |
| **Sysinternals Suite** | [learn.microsoft.com/sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite) | Microsoft's toolkit: Autoruns, Process Monitor, TCPView, and more. **Autoruns alone is worth it.** |
| **Process Hacker / System Informer** | [systeminformer.com](https://systeminformer.com/) | Advanced Task Manager replacement — shows hidden processes, per-process network activity |
| **LatencyMon** | [resplendence.com/latencymon](https://www.resplendence.com/latencymon) | Diagnose real-time latency issues ("my PC lags in games/audio") |
| **WhoCrashed** | [resplendence.com/whocrashed](https://www.resplendence.com/whocrashed) | Identifies drivers causing BSODs |
| **CrystalDiskMark** | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskmark/) | Disk speed benchmark |
| **Windows Terminal** | [github.com/microsoft/terminal](https://github.com/microsoft/terminal) | Modern tabbed terminal — far better than CMD or plain PowerShell |
| **FurMark** | [geeks3d.com/furmark](https://www.geeks3d.com/furmark/) | GPU stress test |
| **Prime95** | [mersenne.org/prime95](https://www.mersenne.org/prime95/) | CPU stress test |
| **Memtest86** | [memtest86.com](https://www.memtest86.com/) | RAM testing — run bootable overnight |

> [!NOTE]
> **Sysinternals Autoruns** lets you see and disable *everything* that starts with Windows — startup entries, scheduled tasks, browser extensions, services, drivers. Nothing hides from it.

---

## 13. Password Managers

A completely unguarded attack surface. Every person you help should have one.

| Tool | Link | Notes |
|---|---|---|
| **Bitwarden** | [bitwarden.com](https://bitwarden.com/) | Open source, cloud-synced, free tier is excellent. Self-hostable with Vaultwarden. |
| **KeePassXC** | [keepassxc.org](https://keepassxc.org/) | Local only, no cloud, encrypted database file. Maximum privacy. |

> [!TIP]
> **Bitwarden** for most people — easy, cross-device, open source. **KeePassXC** for those who don't trust any cloud and want full local control.

---

## 14. Office & Documents

| Tool | Link | Notes |
|---|---|---|
| **LibreOffice** | [libreoffice.org](https://www.libreoffice.org/) | Full office suite — Writer, Calc, Impress. The free answer to Microsoft Office. |
| **OnlyOffice Desktop** | [onlyoffice.com/desktop.aspx](https://www.onlyoffice.com/desktop.aspx) | Better Microsoft Office compatibility than LibreOffice |

---

## 15. PDF Tools

| Tool | Link | Notes |
|---|---|---|
| **Sumatra PDF** | [sumatrapdfreader.org](https://www.sumatrapdfreader.org/) | Ultralight PDF reader (2MB), opens instantly, no bloat. Replaces Adobe Reader completely. |
| **PDF24** | [pdf24.org](https://www.pdf24.org/) | Desktop + web tool: merge, split, compress, convert PDFs. No files uploaded to shady servers. |
| **LibreOffice Draw** | [libreoffice.org](https://www.libreoffice.org/) | Edit PDFs directly, included with LibreOffice |

---

## 16. Media Players & Audio

| Tool | Link | Notes |
|---|---|---|
| **VLC** | [videolan.org/vlc](https://www.videolan.org/vlc/) | Plays everything, every format, every codec. No questions asked. Install this first. |
| **foobar2000** | [foobar2000.org](https://www.foobar2000.org/) | Lightweight, extensible music player. Zero bloat. Highly configurable. |
| **MPC-HC** | [github.com/clsid2/mpc-hc](https://github.com/clsid2/mpc-hc) | Media Player Classic — minimal, fast, open source alternative to VLC |
| **Audacity** | [audacityteam.org](https://www.audacityteam.org/) | Open source audio editor & recorder |

---

## 17. Email Clients

| Tool | Link | Notes |
|---|---|---|
| **Thunderbird** | [thunderbird.net](https://www.thunderbird.net/) | Open source, by Mozilla. Supports Gmail, Outlook, any IMAP/SMTP account. |
| **Mailspring** | [getmailspring.com](https://getmailspring.com/) | Modern UI, free, open source |

---

## 18. Productivity & Notes

| Tool | Link | Notes |
|---|---|---|
| **Obsidian** | [obsidian.md](https://obsidian.md/) | Local Markdown notes, free for personal use. Huge plugin ecosystem. Notes are plain text files — yours forever. |
| **Joplin** | [joplinapp.org](https://joplinapp.org/) | Open source notes with sync (Dropbox, Nextcloud, etc.). Good Evernote replacement. |
| **Notion** | [notion.so](https://www.notion.so/) | Web-based, free tier. Popular for docs, wikis, project tracking. |
| **ShareX** | [getsharex.com](https://getsharex.com/) | Screenshots, screen recording, OCR, annotations. Open source. Way more powerful than Snipping Tool. |

---

## 19. Graphics & Media

### Video Editing

| Tool | Link |
|---|---|
| **DaVinci Resolve** | [blackmagicdesign.com/products/davinciresolve](https://www.blackmagicdesign.com/products/davinciresolve/) |
| **OpenShot** | [openshot.org](https://www.openshot.org/) |
| **Kdenlive** | [kdenlive.org](https://kdenlive.org/) |
| **Pitivi** | [pitivi.org](https://www.pitivi.org/) |
| **Cinelerra-GG** | [cinelerra-gg.org](https://www.cinelerra-gg.org/) |

### Screen Capture & Broadcasting

| Tool | Link |
|---|---|
| **OBS Studio** | [obsproject.com](https://obsproject.com/) |
| **ShareX** | [getsharex.com](https://getsharex.com/) |
| **ScreenPresso** | [screenpresso.com](https://www.screenpresso.com/) |

### Image Editing

| Tool | Link |
|---|---|
| **GIMP** | [gimp.org](https://www.gimp.org/) |
| **Paint.NET** | [getpaint.net](https://www.getpaint.net/) |
| **Inkscape** | [inkscape.org](https://inkscape.org/) |
| **IrfanView** | [irfanview.com](https://www.irfanview.com/) |
| **Aseprite** | [aseprite.org](https://www.aseprite.org/) |
| **Krita** | [krita.org](https://krita.org/) |

### 3D

| Tool | Link |
|---|---|
| **Blender** | [blender.org](https://www.blender.org/) |
| **Wings 3D** | [wings3d.com](http://www.wings3d.com/) |

---

## 20. Text Editors

| Tool | Link |
|---|---|
| **VS Code** | [code.visualstudio.com](https://code.visualstudio.com/) |
| **Notepad++** | [notepad-plus-plus.org](https://notepad-plus-plus.org/) |
| **CudaText** | [cudatext.github.io](https://cudatext.github.io/) |
| **Sublime Text** | [sublimetext.com](https://www.sublimetext.com/) |

---

## 21. Beyond Windows

### Automation & Shortcuts

| Tool | Link |
|---|---|
| **FastKeys** | [fastkeysautomation.com](https://www.fastkeysautomation.com/) |
| **AutoHotkey** | [autohotkey.com](https://www.autohotkey.com/) |

### Virtual Machines

| Tool | Link |
|---|---|
| **VirtualBox** | [virtualbox.org](https://www.virtualbox.org/) |
| **QEMU** | [qemu.org](https://www.qemu.org/) |

### Retro / DOS

**DOSBox** — [dosbox.com](https://www.dosbox.com/) — Retro fun and games without loot boxes or DLCs. The golden age of computing.

### Hackintosh

**Hackintosh.com** — [hackintosh.com](https://hackintosh.com/) — Everything you need to run macOS on unsupported hardware.

---

## 22. Quick Reference — All Tools

| Tool | Link |
|---|---|
| MassGrave (clean ISOs) | [massgrave.dev](https://massgrave.dev) |
| MAS (Windows Activation) | [github.com/massgravel/MAS](https://github.com/massgravel/Microsoft-Activation-Scripts) |
| Rufus | [rufus.ie](https://rufus.ie) |
| **Ventoy** | [ventoy.net](https://www.ventoy.net/) |
| **Hiren's BootCD PE** | [hirensbootcd.org](https://www.hirensbootcd.org/) |
| NVCleanstall | [techpowerup.com/nvcleanstall](https://www.techpowerup.com/nvcleanstall/) |
| AMD Drivers | [amd.com/en/support](https://www.amd.com/en/support/download/drivers.html) |
| Radeon Software Slimmer | [github.com/GSDragoon/RadeonSoftwareSlimmer](https://github.com/GSDragoon/RadeonSoftwareSlimmer) |
| AtlasOS | [atlasos.net](https://atlasos.net) |
| ReviOS | [revi.cc](https://revi.cc) |
| AME Wizard | [ameliorated.io](https://ameliorated.io) |
| ChrisTitus Utility | [christitus.com/win](https://christitus.com/win) |
| uBlock Origin | [ublockorigin.com](https://ublockorigin.com/) |
| **Bitwarden** | [bitwarden.com](https://bitwarden.com/) |
| **KeePassXC** | [keepassxc.org](https://keepassxc.org/) |
| **VLC** | [videolan.org/vlc](https://www.videolan.org/vlc/) |
| **foobar2000** | [foobar2000.org](https://www.foobar2000.org/) |
| **LibreOffice** | [libreoffice.org](https://www.libreoffice.org/) |
| **Sumatra PDF** | [sumatrapdfreader.org](https://www.sumatrapdfreader.org/) |
| **PDF24** | [pdf24.org](https://www.pdf24.org/) |
| **Thunderbird** | [thunderbird.net](https://www.thunderbird.net/) |
| **Obsidian** | [obsidian.md](https://obsidian.md/) |
| **Joplin** | [joplinapp.org](https://joplinapp.org/) |
| **ShareX** | [getsharex.com](https://getsharex.com/) |
| **Sysinternals Suite** | [learn.microsoft.com/sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite) |
| **System Informer** | [systeminformer.com](https://systeminformer.com/) |
| **LatencyMon** | [resplendence.com/latencymon](https://www.resplendence.com/latencymon) |
| **Windows Terminal** | [github.com/microsoft/terminal](https://github.com/microsoft/terminal) |
| **qBittorrent** | [qbittorrent.org](https://www.qbittorrent.org/) |
| Everything (search) | [voidtools.com](https://www.voidtools.com/) |
| RustDesk | [rustdesk.com](https://rustdesk.com/) |
| Snappy Driver Installer | [sdi-tool.org](https://sdi-tool.org/) |
| Ninite | [ninite.com](https://ninite.com/) |
| Chocolatey | [chocolatey.org](https://chocolatey.org/) |
| CrystalDiskInfo | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskinfo/) |
| HWiNFO | [hwinfo.com](https://www.hwinfo.com/) |
| OBS Studio | [obsproject.com](https://obsproject.com/) |
| GIMP | [gimp.org](https://www.gimp.org/) |
| Blender | [blender.org](https://www.blender.org/) |
| VS Code | [code.visualstudio.com](https://code.visualstudio.com/) |
| VirtualBox | [virtualbox.org](https://www.virtualbox.org/) |
| Malwarebytes | [malwarebytes.com](https://www.malwarebytes.com) |

---

## 📌 Version

`v0.2.0` — March 2026 — Added: Rescue tools, Password managers, Office suite, PDF tools, Media players, Email clients, Productivity/Notes, Sysinternals, Process Hacker, LatencyMon, Ventoy, ShareX, qBittorrent, Windows Terminal, foobar2000, Sumatra PDF

---

<div align="center">

*This list is NOT exhaustive, nor does it contain "the TRUE word of GOD himself."*  
*It's just what* works for me™

If you know a better way — send a pull request and improve it!

**For now, this is the way.**

</div>
