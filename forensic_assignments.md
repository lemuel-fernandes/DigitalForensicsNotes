# 🧪 Digital Forensics Assignments - Markdown Report Instructions

Welcome to the **Digital Forensics Lab**. Each task below must be completed independently and uploaded to your GitHub repository.

## 📂 Repository Structure
**Repository Name:** `my-DF-Notes`

**Directory Layout:**
```
my-DF-Notes/
├── exiftool-analysis/
│   ├── report.md
│   ├── Forensics-image.png
│   └── screenshots/
├── virustotal-scan/
│   ├── report.md
│   ├── malware_sample.zip
│   └── screenshots/
├── villain-reverse-shell/
│   ├── report.md
│   └── screenshots/
```

---

## 📸 Assignment 1: ExifTool Image Analysis

### 🔗 Resources
- Image to analyze: [Forensics-image.png](https://github.com/sector21/DigitalForensicsNotes/blob/main/resources/Forensics-image.png)

### ✅ Task
Analyze the metadata of the given image using `exiftool`. Document your findings in a markdown file.

### 📄 Your `report.md` Should Contain:
```markdown
# ExifTool Metadata Analysis Report

## 🔎 Image Overview
- Filename: Forensics-image.png
- File Size: _value_
- Image Dimensions: _value_

## 📸 Camera Info
- Make: _value_
- Model: _value_

## 🌍 Geolocation (If Available)
- GPS Lat/Long: _value_
- Maps Link: [Google Maps](link)

## 🕐 Timestamps
- DateTimeOriginal: _value_
- ModifyDate: _value_

## 📝 Software/Comments
- Editing Software: _value_
- Comment Field: _value_

## 🔐 SHA256 Hash
- `your calculated hash`

## 🧠 Inference
Is the image original? Any signs of manipulation?

## 🖼️ Screenshots
Embed terminal outputs from `exiftool`. Highlight critical sections.
```

---

## 🦠 Assignment 2: VirusTotal File Analysis

### 🔗 Resources
- ZIP File (Password: `infected`): [malware_sample.zip](https://github.com/sector21/DigitalForensicsNotes/blob/main/resources/Forensics-image.png)

### ✅ Task
Upload the sample to [https://virustotal.com](https://virustotal.com), analyze the scan results, and document key findings.

### 📄 Your `report.md` Should Contain:
```markdown
# VirusTotal Analysis Report

## 📁 File Info
- Filename: malware_sample.zip
- File inside: malware_sample.docx
- Hashes:
  - MD5: _value_
  - SHA1: _value_
  - SHA256: _value_

## 🧪 Detection
| Engine | Detection |
|--------|-----------|
| ExampleAV | Trojan.Macro.Gen |

## 📡 Network Indicators
- Domains, IPs flagged

## 📊 Behavioral Summary
- Sandbox behaviors (if any)

## 🗣️ Community Insight
- Votes, user comments

## 🔐 Public Link
- [VirusTotal Public Scan Link](link)

## 🖼️ Screenshots
Include screenshots of your logged-in VT dashboard and scan results.
```

---

## 🖥️ Assignment 3: Villain Framework Reverse Shell

### ✅ Task
Use Villain to simulate a reverse shell attack on your own VM setup. Do **not** use this on real systems or others' devices.

### 📄 Your `report.md` Should Contain:
```markdown
# Villain Framework Reverse Shell Report

## ⚙️ Setup Info
- Payload: `windows/reverse_tcp/powershell`
- LHOST: _your IP_
- LPORT: _your port_

## 🔁 Payload Delivery Method
- Describe how you executed it on the target VM.

## 🖥️ Captured Info
- Hostname: _value_
- IP Address: _value_
- User: _value_

## 🔎 Enumeration Performed
```powershell
whoami
ipconfig
systeminfo
```

## 🛑 Final Verification
Take a screenshot **without executing**, showing you typed in the villain framework shell:
```powershell
echo "https://github.com/<your-github-username>"
```

## 🖼️ Screenshots
Villain shell, session start, IP logs.
```

---

## 📌 Final Notes
- All `report.md` files **must be written in Markdown**.
- Place screenshots in a folder named `screenshots/` inside each assignment directory.
- Do not reuse answers. Every submission is validated with logs, screenshots, hashes.
- Deadline and submission link will be announced in the classroom.

---

If you face any issues, reach out in github by making a issue in the github repo.


Happy Hacking! 🕵️‍♂️

