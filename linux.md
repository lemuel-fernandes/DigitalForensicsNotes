# Linux Forensics

---

## 1. Introduction

* **What is Linux?**

  * UNIX-like, open-source operating system created by Linus Torvalds.
  * Distributed under the GNU General Public License (GPL): free, publicly available source code.
  * Popular choice for enthusiasts and developers: fast, secure alternative to proprietary OS.
* **History**

  * 1991: Linus Torvalds, a student in Helsinki, creates the Linux kernel.
  * Uploaded to the Internet; global community contributions spark the modern Linux ecosystem.
* **Importance in IT**

  * Powers the majority of supercomputers (meteorology, statistics, HPC).

---

## 2. Popular Linux Distributions

Linux “distros” bundle the kernel with tools/configuration. Common examples:

* **Red Hat Linux**
  Commercial distro used by corporations and banks. Powers many Fortune 500 operations.
* **Ubuntu**
  Developed by Canonical; user-friendly for desktops, servers, cloud, and mobile devices.
* **Fedora**
  Community-driven; sponsored by Red Hat. On the leading edge of free/open-source tech.
* **Debian**
  One of the earliest distros (1993). Contains only free software; \~51,000 packages.
* **SUSE**
  German-origin enterprise distro. Early 1994 release makes it one of the oldest.
* **Mint**
  Based on Debian/Ubuntu; elegant GUI, comfortable user experience.
* **Arch Linux**
  Independent, rolling-release, minimalist environment.
* **Linux Lite**
  Debian/Ubuntu base with Xfce; Windows-like UI and preinstalled apps (Dropbox, VLC, LibreOffice).

---

## 3. File System

* **Default:** EXT4 (successor to EXT2/3)

  * Journaling, metadata checksums → improved reliability.
  * **Extents:** contiguous block grouping for efficient allocation.
  * **Inode metadata:** persists until all hard links removed.


<img width="1425" height="453" alt="image" src="https://github.com/user-attachments/assets/2a673396-ddd0-4a8c-a2c9-0fa4a12a5872" />

<img width="1725" height="1012" alt="image" src="https://github.com/user-attachments/assets/a9e39e3d-9d62-4e87-835e-44302f09c83a" />



---

## 4. Forensic Process for Linux Systems

1. **Imaging & Preservation**

   * Identify partitions and devices; acquire bit‑for‑bit images.
2. **Volatile Evidence**

   * RAM capture (LiME, live tools).
3. **Live Forensics**

   * Tools differ: paths, logs, CLI utilities.
4. **Analysis**

   * Similar to Windows but with Linux‑specific artifacts and locations.

---

## 5. Forensic Artifacts

**Important directories**

| Directory   | Description                       |
| ----------- | --------------------------------- |
| `/bin`      | Essential command binaries        |
| `/boot`     | Bootloader files                  |
| `/dev`      | Device files                      |
| `/etc`      | System configuration              |
| `/home`     | User home directories             |
| `/lib`      | Shared libraries & kernel modules |
| `/media`    | Mount points for removable media  |
| `/opt`      | Add-on packages                   |
| `/root`     | Root user home                    |
| `/sbin`     | System binaries                   |
| `/tmp`      | Temporary files                   |
| `/var/logs` | Central log repository            |

---

## 6. Special Artifacts

| Artifact                  | Location                                     |
| ------------------------- | -------------------------------------------- |
| User profile              | `/home/$USER`                                |
| System & application logs | `/etc`                                       |
| OS info                   | `/etc/os-release`                            |
| Install log               | `/root/install.log`                          |
| Hostname                  | `/etc/hostname`                              |
| IP & DNS config           | `/var/log`, `/etc/hosts`, `/etc/resolv.conf` |
| Time zone                 | `/etc/timezone`                              |
| Login history             | `/var/log/auth.log`                          |
| Recently accessed files   | `~/.local/share/recently-used.xbel`          |
| Command history           | `~/.bash_history`                            |

---

## 7. Linux Distributions for Forensic Analysis

### 7.1 Kali Linux

* **Origin:** Formerly BackTrack; Debian‑based.
* **Purpose:** Digital forensics & pentesting.
* **Tools:**

  * **Forensics:** Autopsy, Binwalk, Capstone, chntpw, dc3dd, ddrescue, DFF, diStorm3, Dumpzilla, Extundelete, Foremost, Galleta, Guymager, iPhone backup analyzer, p0f, pdf-parser, pdgmail, REgRipper, Volatility, Xplico
  * **Password:** Acccheck, BruteSpray, CeWL, cisco-auditing-tool, findmyhash

### 7.2 DEFT Linux

* **Purpose:** Law-enforcement & government forensics.
* **Tools:**

  * **Artifact Extraction:** Extractmsg, Readpst, Msgconvert, Rifiuti2, Reglookup, pl, Evtxtract
  * **Data Recovery:** Catfish, Testdisk, Scalpel, Bulk\_extractor
  * **Imaging:** Affcat, Affcopy, Affcrypto, Affsign, Cyclone, Guymager
  * **Hashing:** Ssdeep, Md5deep, sha256sum, sha512sum
  * **Live Forensics:** Evolve, Evtxtract, Rekall, Volatility
  * **Malware Analysis:** Analyzepdf, Balbuzard, Damm, Mastiff, Chkrootkit, Brxor, Clamscan, Yara, Rkhunter, Unxor.py, Cuckoo, Multiscanner
  * **Mobile Forensics:** ADB, Fastboot, Bitpim, Apktool, ipddump, idevicebackup2, iphonebackupanalyzer2
  * **Mount:** Bdemount, Dislocker, vmdkmnt
  * **Network:** ccze, lnav, multitail, CapAnalysis, Driftnet, Ettercap, Nmap, Tshark, Wireshark, Xplico, Kismet, Aircrack-ng
  * **Picture Forensics:** Exifprobe, Vinetto, Outguess, Mat, Stagedetect
  * **Password Recovery:** Cmospwd, Cup, Hashcat, John the Ripper, Pdfcrack, xhydra
  * **Misc:** Maltego, Tinfoleak
  * **Timeline:** Hfind, blkcalc, blkcat, fls, ifind, jcat, mmcat, mactime, sorter, srch\_strings, fiwalk, log2timeline.py, jpeg\_extract, psort.py

### 7.3 Parrot OS

* Debian-based; GUI‑rich anti-forensics and pentesting tools.

### 7.4 Santoku Linux

* Mobile forensics platform (Android/iOS).
* Imaging: NAND, media cards, RAM; mobile malware analysis.

### 7.5 Blackbuntu

* Ubuntu-based; penetration testing & digital forensics.

### 7.6 Paladin Linux

* Ubuntu-based; over 100 forensic tools in 33 categories.

### 7.7 CAINE

* Computer Aided INvestigative Environment; user‑friendly forensic suite.

---

## 8. Challenges in Linux Forensics

* No central Registry (artifacts scattered).
* Deleted-file metadata zeroed → recovery difficulty.
* EXT4 features (extents, checksums) may lack tool support.
* CLI-only tools: steeper learning curve.
* Distro-specific customizations require per-case study.

---

## 9. Windows vs. Linux: Forensics Perspective

| Windows                                      | Linux                                                         |
| -------------------------------------------- | ------------------------------------------------------------- |
| Central Registry stores settings & metadata  | No Registry; config files scattered across `/etc`, logs, etc. |
| Supports FAT/NTFS                            | Supports EXT family, Btrfs, XFS, etc.                         |
| GUI-based tools                              | Primarily CLI-based tools                                     |
| Multiple admin accounts                      | Single `root` account                                         |
| Recycle Bin retains deleted files            | Trash directories; inodes unlinked on delete                  |
| Hardware write blockers                      | Must manually mount devices read-only                         |
| Event logs in `%SystemRoot%\System32\Config` | Logs/config in `/etc`, `/var/log`, etc.                       |

---

## 10. Case Studies

### 10.1 Listing Partitions

1. **Help:** `fdisk -h`

<img width="2695" height="2569" alt="image" src="https://github.com/user-attachments/assets/69250cbc-50bf-43fc-b51c-196d03fe85ab" />

2. **List drives:** `fdisk -l`

<img width="2695" height="1394" alt="image" src="https://github.com/user-attachments/assets/890a9c1b-2baa-4758-a0e6-0cf2729a4110" />

3. **Identify `/dev/sda`, `/dev/sdb`, partitions.**

   * `/dev/sda`: 20 GB, partitions `/dev/sda1`, `/dev/sda2`, `/dev/sda5`.
   * `/dev/sdb`: 5 GB → imaging target.
4. **Image creation:**

   ```bash
   dd if=/dev/sdb of=image.001 bs=1M status=progress
   ```
<img width="2695" height="516" alt="image" src="https://github.com/user-attachments/assets/85315052-5083-4930-9297-0950913cac24" />


### 10.2 Memory Acquisition (LiME)

1. Clone repo: `git clone https://github.com/504ensicsLabs/LiME/`

<img width="1725" height="533" alt="image" src="https://github.com/user-attachments/assets/4a60d9b6-773b-4c75-83f7-a8b1e8347367" />

2. Build: `cd LiME/src && make`

<img width="1725" height="1185" alt="image" src="https://github.com/user-attachments/assets/ab2f3df0-07c2-4d3d-85f5-b0d63627805b" />


3. Capture RAM:

   ```bash
   sudo insmod ./lime-<kernel>.ko "path=../Linux_Memory.mem format=raw"
   ```
<img width="1725" height="461" alt="image" src="https://github.com/user-attachments/assets/89d9faf6-932d-4011-a103-f6dc3b89445b" />

4. Verify:

<img width="1725" height="640" alt="image" src="https://github.com/user-attachments/assets/b3fee2fa-1582-4d23-bf65-db13202534fa" />


### 10.3 Live Forensics (SysScout)

1. Clone & install: `git clone https://github.com/joshbrunty/SysScout`

<img width="1725" height="459" alt="image" src="https://github.com/user-attachments/assets/34f6febd-cb3e-4697-a4cb-0309e5441389" />

2. Run: `bash SysScout.sh`

<img width="1725" height="444" alt="image" src="https://github.com/user-attachments/assets/34480c5e-8801-4899-9c99-813d6b7aa461" />

<img width="1725" height="1214" alt="image" src="https://github.com/user-attachments/assets/5f152b31-98cb-43a9-bac8-ed1becff01cc" />


3. Options:

   * **Option 1:** OS info  
   <img width="1725" height="708" alt="image" src="https://github.com/user-attachments/assets/0d54e1d5-6dde-4c45-85c9-b59d4b2bc0e7" />

   * **Option 2:** Time & timezone 
   <img width="1725" height="750" alt="image" src="https://github.com/user-attachments/assets/352d7315-ffdc-414b-922c-bc3a7ee04de2" />

   * **Option 3:** Hostname & DNS  
   <img width="1725" height="834" alt="image" src="https://github.com/user-attachments/assets/196cbbc9-6ec9-4257-8102-1ac9cc1f6b43" />

   * **Option 4:** IP, routing, MAC  
   <img width="1724" height="1111" alt="image" src="https://github.com/user-attachments/assets/d948b1c2-1cf5-412b-ba23-0fe3ae6c792f" />

   * **Option 5:** Logged-in users 
   <img width="1725" height="711" alt="image" src="https://github.com/user-attachments/assets/f797aa3d-ae4e-4321-ad5b-e5eee35051e8" />

   * **Option 6:** Last logins  
   <img width="1725" height="874" alt="image" src="https://github.com/user-attachments/assets/6aa960b7-4edc-4e69-8ce3-bbf1ca6a15b0" />

   * **Option 7:** RAM & top processes  
    <img width="1725" height="1108" alt="image" src="https://github.com/user-attachments/assets/285503df-41a5-485d-b347-f3be245db66e" />

   

### 10.4 Raw Image Analysis (The Sleuth Kit)

1. **Partition type:** 
<img width="1484" height="1945" alt="image" src="https://github.com/user-attachments/assets/13ad64da-0d30-4259-a24a-b3e5a8f7e7a0" />

2. **FS stats:** 
<img width="1484" height="1945" alt="image" src="https://github.com/user-attachments/assets/51c070b3-a53a-44dd-b166-619c2ded6efb" />

3. **List inodes:** 
<img width="1725" height="741" alt="image" src="https://github.com/user-attachments/assets/6db5b9ab-2119-4e1f-947a-9ee3526f6dd0" />

4. **List files:** 
<img width="1725" height="381" alt="image" src="https://github.com/user-attachments/assets/8ab9a179-fa62-4291-935b-02038b34b196" />

5. **Timestamps:** 
<img width="1725" height="906" alt="image" src="https://github.com/user-attachments/assets/441ab4e4-caa7-4823-a8fd-33da37471375" />

6. **Deleted entries:** 
<img width="1725" height="224" alt="image" src="https://github.com/user-attachments/assets/8ffe8f5d-b0a4-4818-977c-a4a9ec5a93c1" />

7. **Deleted timestamps:** 
<img width="1725" height="903" alt="image" src="https://github.com/user-attachments/assets/47cb16a8-a8cd-4264-a9c4-51dcff1a4525" />


---

## 11. Summary

* Linux: open-source, GPL‑licensed, community‑driven OS.
* Multiple distros for general and forensic use.
* EXT4: default FS with journaling and extents.
* Forensics: imaging, memory capture, live analysis, raw image examination.
* Key artifacts in `/etc`, `/var/log`, `/home`, CLI histories.
* Specialized forensic distros: Kali, DEFT, Parrot, Santoku, etc.
* Challenges: no Registry, metadata wiping, CLI learning curve.
* Windows vs. Linux: architecture and tool differences.

---


