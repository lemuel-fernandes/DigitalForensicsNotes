
# Windows Forensics

## 1. Introduction to Windows Forensics

Microsoft Windows remains the dominant desktop OS worldwide, so most digital forensics tools and methods are developed with Windows in mind. Windows forensics is critical for investigating crimes where digital evidence may exist on Windows devices.

## 2. Digital Evidence in Windows

Digital evidence includes any data stored or transmitted in digital form that can be used in an investigation. In Windows forensics, evidence can be divided into:

- **Volatile Evidence:** Lost when power is off.
- **Non-Volatile Evidence:** Remains when system is shut down.

## 3. Volatile Evidence

Volatile evidence is found in RAM while the system is running.

**Examples:**

- Running processes
- Plain-text passwords
- Unsaved/open files
- Recent chats
- Active network connections

**Best Practice:** Use RAM acquisition tools like Tribble hardware or dumpit utilities to capture RAM before powering off.

## 4. Non-Volatile Evidence

### 4.1 Master File Table (MFT)

- NTFS file system structure containing file metadata.
- Keeps track of file names, sizes, timestamps.
- Deleted file entries marked "to be reused" but data may remain.

**Tool:** FTK Imager, analyzeMFT.

### 4.2 Master Boot Record (MBR)

- First sector on disk.
- Contains bootloader code.
- Magic number: `55AA`.

**Tool:** Hex editors like Hex Workshop.

### 4.3 Windows Registry

- Hierarchical database for configuration data.
- Stores OS, hardware, and user settings.
- Useful for timeline analysis and tracking user activity.

**Tools:** Regshot, RegRipper, Process Monitor, USBDeview.

### 4.4 Event Logs

- Records system, application, and security events.
- Crucial for timeline reconstruction.

**Tools:** EvLog Analyzer, Windows EventLog Analyzer, OSSEC, Syslog-ng.

### 4.5 Other Non-Volatile Artifacts

- **Configuration files:** Include MRU lists (RunMRU, BagMRU).
- **Application files:** Created by programs.
- **Temporary files:** Created during updates and installs.
- **SWAP files:** Pagefile.sys stores data swapped from RAM.
- **Unallocated space:** May contain deleted data.

## 5. File Systems: FAT32 vs NTFS

| Feature | FAT32 | NTFS |
|---------|-------|------|
| Max file size | 4GB | 16TB |
| Fault tolerance | No | Yes |
| Encryption | No | Yes |
| Compression | No | Yes |
| Security | Basic | Advanced |

**NTFS** supports MFT, encryption, and fault tolerance, making it the preferred modern file system.

## 6. NTFS Timestamps

- NTFS tracks MACE: Modify, Access, Create, Entry Modified.
- Registry key `NtfsDisableLastAccessUpdate` can disable access timestamp.

**Detect changes:**

- Use FTK Imager to extract MFT.
- Parse with analyzeMFT.
- Look for mismatches in timestamps.

Attackers can use timestomp to change timestamps.

## 7. Timeline Analysis

Building a timeline helps understand when actions occurred and detect tampering.

## 8. Challenges

- Tool compatibility for different hardware configurations.
- Large drives take time to image.
- Anti-forensics like encryption and log deletion.

## 9. Practical Tools

- **Autopsy:** GUI-based forensics suite.
- **Recuva:** File recovery for deleted files.

## 10. Best Practices

- Always maintain chain of custody.
- Hash evidence.
- Use write blockers.
- Keep detailed notes.

## Summary

Windows forensics involves analyzing both volatile (RAM) and non-volatile (disk) data. Common tools include FTK Imager, Autopsy, RegRipper, and analyzeMFT. Understanding NTFS structures and artifacts is crucial for building timelines and presenting evidence in court.

---
