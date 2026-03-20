# 🖥️ Computer Technician Guide

> *A practical guide to repair, optimize, and maintain your friends and family's computers.*  
> You are "the" tech guy in the family, aren't you?

One of the hallmarks of our age is the decline of the do-it-yourselfer in favor of the hire-an-expert-to-do-it-insteader. Toilet not flushing? Hire a plumber. Porch falling down? Hire a carpenter. Lights on the blink? Hire an electrician.

I'm a Computer Science graduate, so I get often called as "the" tech guy in family and circle of friends. This guide exists so you (and they) never have to pay anyone for something you can do yourself.

---

## 👤 Who am I?

Hi, I'm Alvaro — Software Developer and Computer Science graduate from Argentina, currently living in Costa Rica.

Check my portfolio: **[alvarogonzalezferrer.github.io](https://alvarogonzalezferrer.github.io/)**  
I'm a freelancer, mainly expert in C++. You can hire me for your projects!

---

## 📋 Index

1. [For New Computers — Linux](#-for-new-computers--linux)
2. [For New Computers — Windows](#-for-new-computers--windows)
   - [Step 1 — Choose the right ISO](#step-1--choose-the-right-iso)
   - [Step 2 — Prepare the bootable USB](#step-2--prepare-the-bootable-usb)
   - [Step 3 — Clean GPU drivers](#step-3--clean-gpu-drivers)
   - [Step 4 — Install Windows](#step-4--install-windows)
   - [Step 5 — Optimize the system](#step-5--optimize-the-system)
3. [Remote Desktop](#-remote-desktop)
4. [Cleanup & Debloat](#-cleanup--debloat)
5. [Recover Deleted Data](#-recover-deleted-data)
6. [Backups](#-backups)
7. [Virus & Malware](#-virus--malware)
8. [Disk Health](#-disk-health)
9. [Install / Update Software in Bulk](#-install--update-software-in-bulk)
10. [File Managers & Search](#-file-managers--search)
11. [Hardware Info & Diagnostics](#-hardware-info--diagnostics)
12. [Graphics & Media](#-graphics--media)
13. [Text Editors](#-text-editors)
14. [Beyond Windows](#-beyond-windows)
15. [Quick Reference — All Tools](#-quick-reference--all-tools)

---

## 🐧 For New Computers — Linux

If you want to avoid Windows headaches entirely:

| Distro | Best for | Link |
|---|---|---|
| **Linux Mint** | New computers, Windows-like experience | [linuxmint.com](https://linuxmint.com/) |
| **Kubuntu** | New computers, KDE desktop | [kubuntu.org](https://kubuntu.org/) |
| **Lubuntu** | Old/slow computers | [lubuntu.me](https://lubuntu.me/) |
| **Xubuntu** | Old/slow computers, XFCE desktop | [xubuntu.org](https://xubuntu.org/) |

These come ready out of the box, saving you all the Windows trouble — though you do have some software compatibility trade-offs.

---

## 🪟 For New Computers — Windows

> **Real-world result:** With Chrome (3 windows, 2 tabs each) + Discord + Slack + Spotify + Adobe CC open simultaneously → **107 processes · 18% RAM usage** on a Ryzen 7 5700X3D.  
> A default Windows install would have nearly **triple** the processes.

If someone is charging you to "remove lag and optimize your PC to the max", this section exists so you never need them again.

---

### Step 1 — Choose the right ISO

Download a **clean ISO** directly. Don't modify or debloat the ISO itself — it's a waste of time and resources.

| Version | Description | Best for |
|---|---|---|
| **IoT LTSC** | Lightest version of all. Extremely clean, no bloatware. | Enthusiasts wanting maximum performance |
| **LTSC** | Long-term support. Security updates only. Clean by default. | Users wanting performance without fuss |
| **Consumer (Pro/Home)** | Standard version. More stable but full of preinstalled apps. | Users who need full Microsoft ecosystem |

> [!WARNING]
> **Windows 10** no longer receives feature updates. LTSC versions still get security patches. If you're comfortable managing your own security, **Windows 10 LTSC** is an excellent lightweight option.

> [!NOTE]
> For activation, download and run **[MAS (Microsoft Activation Scripts)](https://github.com/massgravel/Microsoft-Activation-Scripts)**.

📥 Download clean ISOs from **[massgrave.dev](https://massgrave.dev)** — has all clean versions available.

---

### Step 2 — Prepare the bootable USB

Use **[Rufus](https://rufus.ie)** to write the ISO to your USB drive.

If installing **Windows 11**, Rufus offers critical bypass options. Check all of these:

- [x] Remove requirement for 4+ GB RAM, Secure Boot, and TPM 2.0
- [x] Remove requirement for a Microsoft online account
- [x] Create a local account with a custom username
- [x] Disable data collection (skip privacy questions)
- [x] Disable automatic BitLocker device encryption

> [!TIP]
> These options prevent BitLocker from silently encrypting your drive and Windows from forcing an online account — both cause headaches later.

---

### Step 3 — Clean GPU drivers

**Before installing Windows**, prepare a slim driver package on the same USB. Generic drivers Windows installs on first boot can cause conflicts.

#### 🟢 Nvidia GPU — NVCleanstall

1. Download **[NVCleanstall](https://www.techpowerup.com/nvcleanstall/)** — auto-detects the best driver for your GPU.
2. In **components to install**, select only what's needed:
   - [x] Display Driver *(required)*
   - [x] Legacy Control Panel
   - [ ] HD Audio via HDMI *(only if you use audio through monitor/TV)*
3. In the **Tweaks** tab, check the following:
   - [x] Disable Installer Telemetry & Advertising
   - [x] Perform a Clean Installation
   - [x] Disable Multiplane Overlay (MPO)
   - [ ] Unattended Express Installation
   - [ ] Add Hardware Support
   - [ ] Enable DLSS Indicator
4. Click **Build Package** → generates an `.exe` to copy to your USB.

#### 🔴 AMD GPU — Radeon Software Slimmer

1. Download the **WHQL** driver from [AMD's official site](https://www.amd.com/en/support/download/drivers.html).
2. Download **[Radeon Software Slimmer](https://github.com/GSDragoon/RadeonSoftwareSlimmer)** from GitHub.
3. Open Slimmer, load the driver `.exe`.

**`Packages` tab** — uncheck everything except:
- [x] Microsoft Visual C++ 2022 Redistributable 64 bit

Uncheck all HDMI audio packages if you don't need audio through monitor/TV.

**`Scheduled Tasks` tab** — disable all auto-update tasks (AMDInstallLauncher, AMD COMPUTE, AMD Link Driver, etc.).

**`Display Driver Components` tab** — keep only:
- [x] AMD Crash Defender (`amdfendr.inf`)
- [x] AMD-Windows Support Components (`amdwin-u0198634.inf`)

4. Click **Modify Installer** → copy the output folder to the USB.

---

### Step 4 — Install Windows

1. Boot from the USB and follow the normal installation process.
2. **When Windows is about to start for the first time** — disconnect Ethernet or disable WiFi. Don't let generic drivers or updates install yet.
3. **Windows 10 only** — when it asks for a Microsoft account, press `Shift + F10` and run:

```
OOBE\BYPASSNRO
```

The PC reboots. Continue normally and create a local account.

4. Inside Windows, install your prepared GPU drivers (quick install). Reboot.
5. Reconnect to the internet.

---

### Step 5 — Optimize the system

Three approaches — pick one or combine them:

| Option | Method | Aggressiveness | Best for |
|---|---|---|---|
| **A** | Playbooks (AtlasOS / ReviOS) | 🔴 High | Maximum performance |
| **B** | ChrisTitus Script | 🟡 Medium | Easy and effective |
| **A + B** | Both combined | 🔴🔴 Maximum | Enthusiasts |

---

#### Option A — Playbooks (AtlasOS / ReviOS)

Playbooks deeply modify Windows via scripts, registry edits, and service injection — leaving only what's essential.

| | **AtlasOS** | **ReviOS** |
|---|---|---|
| **Focus** | Stability | Maximum performance |
| **Windows 10** | ❌ Not supported | ✅ Supported |
| **Windows 11** | ✅ Supported | ✅ Supported |
| **Download** | [atlasos.net](https://atlasos.net) | [revi.cc](https://revi.cc) |

**Steps:**

1. Download the **Playbook** and **[AME Wizard](https://ameliorated.io)**.
2. Unzip both and open AME Wizard.
3. Drag the Playbook into AME Wizard and follow the prompts (Defender, browser, privacy options).
4. PC reboots automatically when done. ✅

---

#### Option B — ChrisTitus Script

Open **PowerShell as Administrator** and run:

```powershell
irm "https://christitus.com/win" | iex
```

In the **Tweaks** tab, enable the following:

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

**⚠️ Advanced Tweaks** *(pick based on your needs)*

- [x] Disable Microsoft Copilot
- [x] Remove Microsoft Edge
- [x] Remove OneDrive
- [x] Remove Xbox & Gaming Components
- [ ] Remove ALL MS Store Apps — ⛔ Not recommended

**🔧 Customize Preferences** *(recommended)*

- [x] Dark Theme for Windows
- [x] Disable Multiplane Overlay
- [x] Modern Standby Fix
- [x] Show File Extensions

**🏎️ Performance Plans — don't skip:**

```
→ Add and Activate Ultimate Performance Profile
```

> [!IMPORTANT]
> If you removed Edge and have no browser: the **first tab** of the script lets you install Chrome, Firefox, Brave, etc.

Reboot when done. ✅

---

#### Bonus — Overclock & Undervolt

| Technique | What it does | Result |
|---|---|---|
| **Overclock** | Increases CPU/GPU/RAM frequency above factory spec | More raw performance |
| **Undervolt** | Reduces voltage while maintaining performance | Less heat, less power draw, more stability |

> [!NOTE]
> These are **one-on-one** because every component varies. There's no universal recipe — you need to measure and adjust per your specific CPU/GPU.

---

## 🌐 Remote Desktop

Because the family member in trouble is usually on the other side of the globe at 3am:

| Tool | Link | Notes |
|---|---|---|
| **RustDesk** | [rustdesk.com](https://rustdesk.com/) | Open source, self-hostable |
| **AnyDesk** | [anydesk.com](https://anydesk.com/) | Fast, lightweight |
| **TeamViewer** | [teamviewer.com](https://www.teamviewer.com/) | Classic, feature-rich |
| **UltraVNC** | [uvnc.com](https://uvnc.com/) | Open source, LAN-focused |

---

## 🧹 Cleanup & Debloat

I usually have a script pack ready. Download, run, done.

| Tool | Link | Purpose |
|---|---|---|
| **Bulk Crap Uninstaller** | [bcuninstaller.com](https://www.bcuninstaller.com/) | Mass uninstall apps |
| **BleachBit** | [bleachbit.org](https://www.bleachbit.org/) | Deep disk cleanup |
| **Privatezilla** | [github.com/builtbybel/privatezilla](https://github.com/builtbybel/privatezilla) | Disable Windows telemetry & spyware |
| **DoNotSpy11** | [pxc-coding.com/donotspy11](https://pxc-coding.com/donotspy11/) | Disable Win11 telemetry |
| **LockHunter** | [lockhunter.com](https://lockhunter.com/) | Delete files that refuse to be deleted |
| **Czkawka** | [github.com/qarmin/czkawka](https://github.com/qarmin/czkawka) | Remove unnecessary & duplicate files |
| **dupeGuru** | [dupeguru.voltaicideas.net](https://dupeguru.voltaicideas.net/) | Find duplicate files |
| **WinDirStat** | [windirstat.net](https://windirstat.net/) | Disk usage visualizer & cleanup |
| **Defraggler** | [ccleaner.com/defraggler](https://www.ccleaner.com/defraggler/) | Disk defrag *(HDDs only — never defrag an SSD)* |
| **Open-Shell** | [github.com/Open-Shell/Open-Shell-Menu](https://github.com/Open-Shell/Open-Shell-Menu) | Classic Start menu replacement for Win 10/11 |

---

## 🗂️ Recover Deleted Data

I try to avoid this task. Please have **BACKUPS** and educate your family about them.

| Tool | Link | Notes |
|---|---|---|
| **Recuva** | [ccleaner.com/recuva](https://www.ccleaner.com/recuva/) | Recover deleted files |
| **TestDisk / PhotoRec** | [cgsecurity.org](https://www.cgsecurity.org/wiki/TestDisk) | Powerful open-source recovery |
| **Autopsy** | [sleuthkit.org/autopsy](https://www.sleuthkit.org/autopsy/) | Full digital forensics platform |

More alternatives: [alternativeto.net/software/recuva](https://alternativeto.net/software/recuva/)

---

## 💾 Backups

### The 3-2-1 Rule

An easy acronym that covers almost any failure scenario:

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

## 🦠 Virus & Malware

My approach: run a full scan + immunization, then remove the scanner and leave only Windows Defender. Most family hardware is modest and a full-time AV tends to slow it down.

### Scanners

| Tool | Link | Notes |
|---|---|---|
| **Windows Defender** | Built-in | Leave this as the permanent AV |
| **Avira Free** | [avira.com](https://www.avira.com/en/free-antivirus-windows) | Good free scanner |
| **Spybot Free** | [safer-networking.org](https://www.safer-networking.org/products/spybot-free-edition/) | Has a great "immunization" feature — use it |
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
> In Chrome or Firefox, always install **[uBlock Origin](https://ublockorigin.com/)** — it's a must.

---

## 🔍 Disk Health

| Tool | Link | Notes |
|---|---|---|
| **CrystalDiskInfo** | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskinfo/) | S.M.A.R.T. health monitoring |
| **HDDScan** | [hddscan.com](https://hddscan.com/) | Deep scan for HDD/SSD/NVMe |
| **chkdsk** | Built into Windows | Run `chkdsk /f /r` in CMD as admin |

---

## 📦 Install / Update Software in Bulk

Save time — install and update everything at once.

| Tool | Link | Notes |
|---|---|---|
| **Winget** | Built into Windows 11 | Official Microsoft package manager |
| **Ninite** | [ninite.com](https://ninite.com/) | Simple bulk installer, no bloat |
| **Chocolatey** | [chocolatey.org](https://chocolatey.org/) | CLI package manager |
| **Patch My PC** | [patchmypc.com](https://patchmypc.com/home-updater) | Auto-update installed software |
| **Snappy Driver Installer** | [sdi-tool.org](https://sdi-tool.org/) | Offline driver installer |
| **Just Install** | [github.com/just-install/just-install](https://github.com/just-install/just-install) | Minimal CLI installer |

---

## 📁 File Managers & Search

| Tool | Link | Notes |
|---|---|---|
| **Everything** | [voidtools.com](https://www.voidtools.com/en-us/) | Instant file search — far better than Windows Search |
| **Explorer++** | [explorerplusplus.com](https://explorerplusplus.com/) | Tabbed Windows Explorer replacement |
| **Total Commander** | [ghisler.com](https://www.ghisler.com/) | Dual-pane, very powerful |
| **Far Manager** | [farmanager.com](https://www.farmanager.com/) | Console-style dual-pane |
| **MultiCommander** | [multicommander.com](http://multicommander.com/) | Feature-rich dual-pane |
| **Meld** | [meldmerge.org](https://meldmerge.org/) | Merge/compare files, dirs, and version-controlled repos |

---

## 🔧 Hardware Info & Diagnostics

| Tool | Link | Purpose |
|---|---|---|
| **HWiNFO** | [hwinfo.com](https://www.hwinfo.com/) | Detailed hardware info & real-time sensors |
| **Speccy** | [ccleaner.com/speccy](https://www.ccleaner.com/speccy) | Quick hardware overview |
| **CPU-Z** | [cpuid.com/softwares/cpu-z.html](https://www.cpuid.com/softwares/cpu-z.html) | CPU, RAM, motherboard details |
| **GPU-Z** | [techpowerup.com/gpuz](https://www.techpowerup.com/gpuz/) | GPU details |
| **WhocrashED** | [resplendence.com/whocrashed](https://www.resplendence.com/whocrashed) | Identifies drivers causing BSODs |
| **CrystalDiskMark** | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskmark/) | Disk speed benchmark |
| **FurMark** | [geeks3d.com/furmark](https://www.geeks3d.com/furmark/) | GPU stress test |
| **Prime95** | [mersenne.org/prime95](https://www.mersenne.org/prime95/) | CPU stress test |

---

## 🎨 Graphics & Media

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
| **ScreenPresso** | [screenpresso.com](https://www.screenpresso.com/) |

### Image Editing & Graphics

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

## 📝 Text Editors

| Tool | Link |
|---|---|
| **VS Code** | [code.visualstudio.com](https://code.visualstudio.com/) |
| **Notepad++** | [notepad-plus-plus.org](https://notepad-plus-plus.org/) |
| **CudaText** | [cudatext.github.io](https://cudatext.github.io/) |
| **Sublime Text** | [sublimetext.com](https://www.sublimetext.com/) |

---

## 🌍 Beyond Windows

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

### Retro & DOS

**DOSBox** — [dosbox.com](https://www.dosbox.com/) — Retro fun and games without loot boxes or DLCs. The golden age of computing.

### Hackintosh

**Hackintosh.com** — [hackintosh.com](https://hackintosh.com/) — Everything you need to run macOS on unsupported hardware.

---

## 📚 Quick Reference — All Tools

| Tool | Link |
|---|---|
| MassGrave (clean ISOs) | [massgrave.dev](https://massgrave.dev) |
| MAS (Windows Activation) | [github.com/massgravel/Microsoft-Activation-Scripts](https://github.com/massgravel/Microsoft-Activation-Scripts) |
| Rufus | [rufus.ie](https://rufus.ie) |
| NVCleanstall | [techpowerup.com/nvcleanstall](https://www.techpowerup.com/nvcleanstall/) |
| AMD Drivers (official) | [amd.com/en/support](https://www.amd.com/en/support/download/drivers.html) |
| Radeon Software Slimmer | [github.com/GSDragoon/RadeonSoftwareSlimmer](https://github.com/GSDragoon/RadeonSoftwareSlimmer) |
| AtlasOS | [atlasos.net](https://atlasos.net) |
| ReviOS | [revi.cc](https://revi.cc) |
| AME Wizard | [ameliorated.io](https://ameliorated.io) |
| ChrisTitus Windows Utility | [christitus.com/win](https://christitus.com/win) |
| uBlock Origin | [ublockorigin.com](https://ublockorigin.com/) |
| Snappy Driver Installer | [sdi-tool.org](https://sdi-tool.org/) |
| Ninite | [ninite.com](https://ninite.com/) |
| Chocolatey | [chocolatey.org](https://chocolatey.org/) |
| Everything (file search) | [voidtools.com](https://www.voidtools.com/) |
| RustDesk | [rustdesk.com](https://rustdesk.com/) |
| CrystalDiskInfo | [crystalmark.info](https://crystalmark.info/en/software/crystaldiskinfo/) |
| HWiNFO | [hwinfo.com](https://www.hwinfo.com/) |
| OBS Studio | [obsproject.com](https://obsproject.com/) |
| GIMP | [gimp.org](https://www.gimp.org/) |
| Blender | [blender.org](https://www.blender.org/) |
| VS Code | [code.visualstudio.com](https://code.visualstudio.com/) |
| VirtualBox | [virtualbox.org](https://www.virtualbox.org/) |

---

## 📌 Version

`v0.1.0` — March 2026 — Merged PC optimization guide + repaired and completed all links

---

<div align="center">

*This list is NOT exhaustive, nor does it contain "the TRUE word of GOD himself."*  
*It's just what* works for me™

If you know a better way — send a pull request and improve it!

**For now, this is the way.**

</div>
