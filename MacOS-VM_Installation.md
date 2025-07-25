# Install macOS Big Sur on VirtualBox (Windows 10/11)

A complete step-by-step guide to install macOS Big Sur using VirtualBox on a Windows system.

---

## Minimum System Requirements

| Component    | Requirement       |
| ------------ | ----------------- |
| OS           | Windows 10/11     |
| CPU          | 8 Core            |
| RAM          | 16 GB             |
| Storage      | 100 GB free space |
| Connectivity | Internet Access   |

---

## Step 1: Download Required Tools

### VirtualBox & Extension Pack

* **Download Link:** [VirtualBox Download Page](https://www.virtualbox.org/wiki/Downloads)

Ensure you also download the **VirtualBox Extension Pack** corresponding to your VirtualBox version.

### macOS Big Sur ISO

* **Recommended Version:** Big Sur (others may fail)
* **Download Link:** [macOS Big Sur ISO – Archive.org](https://archive.org)

---

## Pre-Configuration: Disable Memory Integrity & Hyper-V

### 1. Disable Memory Integrity

* Go to **Start > Windows Security > Device Security > Core Isolation**
* Toggle **Memory Integrity** to **OFF**

### 2. Disable Hyper-V

Open Command Prompt as Administrator and run:

```bash
bcdedit /set hypervisorlaunchtype off
```

 **Restart** your PC after this step.

---

## Step 2: Create a New Virtual Machine

### Launch VirtualBox and:

1. Click **"New"**
2. Name your VM (you’ll need this later)
3. Select downloaded **ISO** file
4. Type: `Mac OS X`, Version: `Mac OS X (64-bit)`
5. **Memory:** At least 4096 MB (4 GB)
6. **CPU:** Minimum 4 CPUs
7. **Disk Size:** 80–150 GB
8. Finish VM creation

### Configure VM Settings:

* Go to **Settings > Display**
* Set **Video Memory** to `128 MB`
* Close VirtualBox

---

## Step 3: Configure macOS VM using VBoxManage

### Open Command Line as Administrator:

Navigate to your VirtualBox installation directory. Example:

```bash
cd "C:\Program Files\Oracle\VirtualBox"
```

Or your custom path:

```bash
cd D:\VirtualBox\
```

### Run the Following Commands:

Replace `"VM Name"` with the exact name of your VM.

```bash
./VBoxManage.exe modifyvm "VM Name" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff

./VBoxManage.exe setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac19,3"

./VBoxManage.exe setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"

./VBoxManage.exe setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"

./VBoxManage.exe setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"

./VBoxManage.exe setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 0

# Only for AMD Processors:
./VBoxManage.exe modifyvm "VM Name" --cpu-profile "Intel Core i7-6700K"

./VBoxManage.exe setextradata "VM Name" "VBoxInternal/TM/TSCMode" "RealTSCOffset"
```

After running all commands, close the terminal.

---

## Step 4: Start and Install macOS

* Launch **VirtualBox**
* Select your VM
* Click **Start**
* macOS setup should now begin!

---

## (Optional) Disk Not Found? Fix It:

### Follow these steps inside macOS Installer:

1. Open **Disk Utility** from the toolbar.
2. Click **View > Show All Devices**
3. Select **VBOX HARDDISK Media** (top-level disk)
4. Click **Erase** and use the following settings:

| Setting | Value              |
| ------- | ------------------ |
| Name    | Macintosh HD       |
| Format  | APFS               |
| Scheme  | GUID Partition Map |

5. Click **Erase**, then close Disk Utility
6. You should now see `Macintosh HD` in the disk list
7. Continue macOS installation!

---

## Done!

You have now successfully installed macOS Big Sur on VirtualBox. Follow the setup screen and enjoy macOS on your Windows machine!

---

> **Troubleshooting Tips**:
>
> * Ensure Hyper-V and memory integrity are disabled
> * Always run commands **as Administrator**
> * If performance is poor, your host machine may lack GPU acceleration (VirtualBox has limited support for macOS graphics)

---
