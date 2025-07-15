# Digital Evidence Categories

| **Category**   | **Definition**                   | **Key Examples**                                                                 |
|----------------|----------------------------------|----------------------------------------------------------------------------------|
| **Volatile**   | Lost when power is removed       | Running processes, clear-text passwords, open/unsaved files, recent chats, active network connections |
| **Non-volatile** | Survive power-off; stored on disks or other media | $MFT, MBR, Registry hives, logs, configuration files, application & temp files, unallocated space |

---

## 2. Volatile Artifacts (RAM)

- **Running Processes** – List of executables currently in memory.
- **Clear-text Passwords** – Sometimes left by apps or browsers.
- **Open/Unsaved Documents** – Recoverable drafts.
- **Recent Chats & Network Connections** – Help reconstruct user activity.

> **Tip:** Perform a live memory capture before shutting the system down.

---

## 3. Non-Volatile Artifacts

### 3.1 Master Boot Record (MBR)

- First sector of a disk; stores bootloader & partition table.
- Ends with hex signature `55 AA` (the “magic number”).

### 3.2 Master File Table ($MFT)

- NTFS file that records every file’s name, size, timestamps, etc.
- Entries marked “to be reused” when a file is deleted—remains until overwritten.

### 3.3 Windows Registry

- Central database for OS, hardware, and application settings.

**Valuable keys:**
- **RunMRU** – Commands typed in the Run dialog.
- **BagMRU/Shell Bags** – Folder view & access history.

**Tools:** Regshot, RegRipper, Process Monitor, MUICacheView.

### 3.4 Event Logs

- **System** (OS events)
- **Application** (program activity)
- **Recently Accessed Files / Command History**

**Analyzers:** EvLog 3.0, Windows EventLog Analyzer, OSSEC, syslog-ng, log2timeline.

---

## 4. File Systems Overview

| **Feature**          | **FAT32**    | **NTFS**                           |
|----------------------|---------------|------------------------------------|
| Max file size        | 4 GB          | 16 TB+                             |
| Security & ACLs      | None          | Yes (permissions, encryption)      |
| Fault tolerance      | Lacking       | Journaling & self-healing          |
| Compression          | Not supported | Supported                          |
| Forensics use        | Easy wipe/partition media | Rich metadata ($MFT), timestamps |

---

## 5. NTFS Timestamp (MACE) Analysis

- **M**odified, **A**ccessed, **C**reated, **E**ntry Modified.
- Last Access updates disabled by default via `NtfsDisableLastAccessUpdate = 1` (Registry).
- Attackers change timestamps with **timestomp**; investigators compare `StdInfo` vs `FN` timestamps in the `$MFT` to detect tampering.

---

## 6. Acquisition Techniques

- **Disk-to-Image** – Full forensic image (preferred).
- **Disk-to-Disk** – Clone when imaging isn’t possible.
- **Logical** – Capture only chosen files.
- **Sparse** – Grab fragments from deleted/unallocated areas.

---

## 7. Essential Tools & Workflows

| **Task**                | **Tool**        | **Core Steps**                                                                 |
|-------------------------|-----------------|--------------------------------------------------------------------------------|
| Registry change tracking | Regshot         | Snapshot 1 → install/change → Snapshot 2 → Compare to list new/modified keys. |
| Export $MFT             | FTK Imager      | Logical drive view → export hidden `$MFT` file; unhide with `attrib -s -h`.   |
| Parse $MFT              | analyzeMFT.py   | `python analyzeMFT.py -f $MFT -o mft.csv -e` to get CSV with timestamps.      |
| Full image analysis     | Autopsy         | New case → add image → select ingest modules → browse artifacts → tag & report. |
| File recovery           | Recuva          | Wizard → select file types & location → scan deleted files → recover to new drive. |

---

## 8. Timeline Analysis

- Combine RAM data, logs, file timestamps, Registry MRUs, etc., into a single timeline.
- Cross-check evidence; spot anti-forensic gaps or out-of-sequence events.

---

## 9. Common Challenges

- Tool compatibility with diverse hardware/drivers.
- Large disks (1 TB+) increase imaging time and storage needs.
- Encryption/firmware locks may block access.
- Anti-forensic tactics (log wiping, timestamp spoofing) require validating data via multiple sources.

---

## Memory Aids

- **“V-RAM”** – Volatile evidence lives in RAM.
- **“55 AA = boot OK”** – MBR signature.
- **“MACE your case”** – Always check NTFS Modify–Access–Create–Entry values.
- **“Shoot-Diff-Compare”** – Regshot workflow.

---
