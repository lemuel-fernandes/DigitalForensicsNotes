# Digital Forensics and Malware Detection.

## Session Overview
- **Duration:** 2 Hours
- **Purpose:** To learn fundamentals of digital forensics and basics of malware detection techniques.

---

## 1. Introduction to Digital Forensics

### What is Digital Forensics?
Digital Forensics is the process of identifying, preserving, analyzing, and presenting digital evidence in a legally acceptable manner.

**Example Scenario:**
- A company suspects an employee leaked confidential data.
- Forensic experts collect computer logs, email records, and USB access logs as evidence.

### Importance of Digital Forensics
- Helps solve cybercrimes.
- Maintains integrity and confidentiality of sensitive data.
- Provides evidence for legal proceedings.

### Key Terms
- **Chain of Custody:** A documented record of everyone who handled the evidence.
- **Forensic Readiness:** Preparing an organization to handle forensic investigations.
- **Types of Evidence:**
  - Disk Images
  - RAM Dumps
  - Logs
  - Network Traffic

### Digital Forensic Process

| Step          | Description                          |
|---------------|--------------------------------------|
| Identification| Recognize incident and evidence source |
| Preservation  | Secure and protect evidence          |
| Collection    | Acquire data without altering it     |
| Examination   | Inspect data for important information |
| Analysis      | Interpret and reconstruct events     |
| Reporting     | Present findings in reports          |

**Example Scenario:**
- Identifying unauthorized access on a web server.
- Collecting server logs.
- Analyzing logins and IP addresses.

---

## 2. Introduction to Malware and Detection Techniques

### What is Malware?
Malware (Malicious Software) is any program designed to harm or exploit systems, networks, or users.

### Types of Malware

| Type      | Description                           | Real-World Example        |
|-----------|---------------------------------------|--------------------------|
| Virus     | Attaches to clean files and spreads   | Michelangelo Virus       |
| Worm      | Self-replicates without user action   | Stuxnet Worm             |
| Trojan    | Disguises as legitimate software      | Zeus Trojan              |
| Spyware   | Monitors user activity                | Pegasus Spyware          |
| Ransomware| Encrypts files and demands payment    | WannaCry Ransomware      |
| Rootkits  | Hides presence of malware             | Sony Rootkit Scandal     |

### Malware Lifecycle
1. **Delivery**: Malware is delivered via email, website, or USB.
2. **Execution**: The user runs the infected file.
3. **Persistence**: Malware stays active across reboots.
4. **Communication**: Sends data to attacker.
5. **Damage**: Steals, encrypts, or destroys data.

**Scenario Example:**
- Opening a suspicious email attachment installs ransomware.

### Malware Detection Techniques
- **Static Analysis:** Examining the malware code without running it.
- **Dynamic Analysis:** Running malware in a controlled environment (sandbox) to observe behavior.
- **Signature-Based Detection:** Matches known malware patterns.
- **Heuristic-Based Detection:** Detects based on abnormal behavior.
- **Behavioral Analysis:** Monitors system behavior in real-time.

### Static vs Dynamic Analysis Table

| Analysis Type | Characteristics                  | Example Tool    |
|---------------|---------------------------------|-----------------|
| Static        | No execution required            | PEStudio        |
| Dynamic       | Executes in sandbox environment  | Cuckoo Sandbox  |

---

## 3. Tools Overview

### Forensics Tools
- **Autopsy:** Digital forensic platform for analyzing hard drives, smartphones.
- **FTK Imager:** Creates forensic images of data.
- **Wireshark:** Network traffic analysis.

### Malware Detection Tools
- **VirusTotal:** Scans files and URLs for viruses.
- **Hybrid Analysis:** Dynamic analysis reports.
- **PEStudio:** Static malware inspection.
- **ExifTool:** Extract metadata from files.

---

## 4. Hands-On Exercise

### VirusTotal Usage Example
- Step 1: Go to [https://www.virustotal.com](https://www.virustotal.com)
- Step 2: Upload a sample file.
- Step 3: Observe the report:
  - Detection Rate: How many engines detect it as malicious.
  - File Hash: Unique identifier.
  - Community Comments: Insight from other users.

**Activity Summary:**
- Practice uploading dummy files.
- Review detection labels.
- Discuss what information is most useful.

---

## 5. Wrap-Up

### Key Takeaways
- Digital forensics helps identify and investigate cyber incidents.
- Malware detection uses static and dynamic analysis techniques.
- Practical tools include Autopsy, VirusTotal, PEStudio.

---

End of Notes
