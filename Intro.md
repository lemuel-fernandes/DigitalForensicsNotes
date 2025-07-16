# DIGITAL FORENSICS STUDENT NOTES

## 1. Understanding Cyberspace and Cybercrime

### What is Cyberspace?

* **Definition:** Cyberspace is the virtual environment where digital communications and computer systems exist and interact.
* **Impact:**

  * Growth of IT industries, creating millions of jobs.
  * **E-commerce:** Revolutionized shopping through platforms like Amazon, Flipkart.
  * **E-Governance:** Online portals for taxes, licenses, ensuring transparency.

### Rise of Cybercrime

* **Definition:** Unlawful acts where a computer is used as a tool, a target, or both.
* **Examples:** Hacking, phishing, ransomware.
* **Real-World Example:**

  * 2017 WannaCry ransomware infected 200,000 computers in 150 countries, including the UK NHS.

## 2. Introduction to Cyber Forensics

### Definition

* Cyber Forensics involves investigation, analysis, and preservation of digital evidence.
* **Objective:** Ensure evidence is admissible in court.
* **Other Terms:** Computer Forensics, Electronic Discovery, Digital Forensics.

### What Does It Involve?

* Identify and collect digital evidence.
* Analyze hidden folders, unallocated space.
* Recover deleted, encrypted, or damaged files.
* Generate clear reports for legal use.

**Keywords:** Chain of Custody, Imaging, Hashing.

## 3. Brief History of Cyber Forensics

| Year   | Milestone                                               |
| ------ | ------------------------------------------------------- |
| 1980s  | IBM PCs launch — rise of computer hobbyists.            |
| 1984   | FBI Magnetic Media Program started, became CART.        |
| 1987   | Access Data formed, a pioneer in forensic tools.        |
| 1993   | 1st International Conference on Computer Evidence.      |
| 1995   | IOCE formed for global collaboration.                   |
| 2002   | SWGDE published Best Practices for Computer Forensics.  |
| 2004   | Budapest Convention on Cybercrime signed.               |
| 2005   | ISO 17025: Competence guidelines for forensic labs.     |
| Modern | EnCase, FTK, Sleuth Kit, Autopsy became standard tools. |

## 4. Cyber Forensics Investigation Process

### Why a Structured Process?

* Ensures integrity, accuracy, and legality.
* Makes findings understandable for non-technical stakeholders.

### Forensic Investigation Steps

1. **Incident:** The crime event; devices involved include PCs, smartphones, IoT.
2. **Identification:** Define scope — suspects, sources of evidence.
3. **Seizure:** Collect physical devices using legal procedures.
4. **Imaging:** Create a bit-stream copy (e.g., .dd, .E01 formats).
5. **Hashing:** Generate digital fingerprint (MD5, SHA-1, SHA-256).
6. **Analysis:** Examine image for deleted files, hidden malware, logs.
7. **Reporting:** Write objective, clear, understandable reports.
8. **Preservation:** Store evidence safely; isolate devices if needed.

**Process Flow:** Incident → Identification → Seizure → Imaging → Hashing → Analysis → Reporting → Preservation.

## 5. Forensic Protocol for Evidence Acquisition

* Purpose: Preserve evidence integrity.
* Standard steps apply for Windows, Linux, Mac.
* Choose evidence types based on the crime.
* Use **write blockers** to prevent data alteration.

## 6. Digital Forensics Standards & Guidelines

| Organization | Role                                 |
| ------------ | ------------------------------------ |
| NIST         | National standards.                  |
| IOCE         | International sharing.               |
| ASCLD        | Crime lab accreditation.             |
| SWGDE        | Best practices for digital evidence. |
| ISO SC 27    | Security techniques.                 |

## 7. Digital Evidence

### What is Digital Evidence?

* Any data stored/transmitted via electronic devices.
* Examples: Hard drives, phones, USBs, cloud storage, network logs.

### Characteristics

* **Latent:** Not obvious.
* **Cross-jurisdictional:** Data travels easily.
* **Easily altered or destroyed.**
* **Time-sensitive:** Data can disappear quickly.

## 8. Tools & Best Practices

### Write Blockers

* Prevent accidental writes to drives.
* **Types:**

  * Native (same interface): IDE to IDE.
  * Tailgate (different interfaces): Firewire to SATA.

### Forensic Triage

* Prioritize important evidence.
* Saves time and resources.

### Chain of Custody

* Tracks who handled evidence throughout its lifecycle.
* Must include:

  * Device details.
  * Timestamps.
  * Names of handlers.
  * Transfers and locations.

## 9. Types of Cybercrimes

1. **Malware Attacks:** Viruses, worms, Trojans, ransomware.
2. **Malvertising:** Malicious ads infecting devices.
3. **Phishing:** Fake emails/websites to steal information.
4. **Cyberstalking:** Harassing or threatening via online channels.
5. **Fake Profiles:** Using AI-generated faces or stolen identities.
6. **Web Defacement:** Altering a website's visual appearance.
7. **Web Jacking:** Taking control of a website's DNS.
8. **Juice Jacking:** Malware via public USB charging ports.
9. **DDoS:** Overloading servers with traffic.
10. **Software Piracy:** Using cracked or unlicensed software.
11. **Formjacking:** Stealing payment details through compromised forms.

## 10. Notable Case Studies

| Case                 | Description                                                | Lesson                                 |
| -------------------- | ---------------------------------------------------------- | -------------------------------------- |
| SIM Swap (India)     | Businessman lost \$260,000 due to fake telecom calls.      | Always verify SIM swaps.               |
| Crypto SIM Swap (US) | Hacker stole \$5 million in crypto, sentenced to 10 years. | Cybercriminals face real penalties.    |
| ATM Cloning (India)  | Employee stole \$70,000 with card skimmers.                | Be careful with card swipes.           |
| Email Fraud (Europe) | Man lost €36,000 after email hack.                         | Use strong passwords, secure networks. |
| Google Nest Guard    | Hidden microphone discovered in device.                    | Be cautious with smart devices.        |

## 11. Challenges in Cyber Forensics

| Challenge        | Explanation                                      |
| ---------------- | ------------------------------------------------ |
| Encryption       | Data is hidden or unreadable without keys.       |
| Cloud Forensics  | Data stored online depends on service providers. |
| Data Volume      | Larger drives take longer to image and store.    |
| Legal Issues     | Jurisdiction and privacy laws vary.              |
| IoT Devices      | Low-security smart devices are vulnerable.       |
| Lack of Training | Shortage of skilled investigators.               |
| Cross-Border     | International cooperation can be complex.        |
| SSD Forensics    | Features like TRIM make recovery difficult.      |

## 12. Skills Needed to Become a Cyber Forensic Expert

* **Observation and Analysis:** Detect hidden evidence.
* **Critical Thinking:** Solve complex problems.
* **Organization:** Keep detailed, clear records.
* **Communication:** Write clear reports and testify in court.
* **Continuous Learning:** Stay updated with new attacks and tools.

### Certifications

* **Vendor-Neutral:** Certified Computer Examiner (CCE).
* **Vendor-Specific:** EnCase Certified Examiner (EnCE).

## 13. Cyber Forensic Tools

| Type          | Examples            | Pros & Cons                                  |
| ------------- | ------------------- | -------------------------------------------- |
| Closed Source | EnCase, FTK         | Easy to use, expensive, licensed.            |
| Open Source   | Sleuth Kit, Autopsy | Customizable, community support, often free. |

## 14. Cybersecurity Trends

* GDPR compliance impacts.
* Growth of cloud vulnerabilities.
* Rise of IoT device risks.
* Increase in DDoS attacks.
* Boardroom cybersecurity discussions.
* Strong cyber hygiene awareness.

## Key Takeaways

* Cyber Forensics combines investigation, law, and technology.
* Always maintain a proper chain of custody.
* Use reliable tools and follow standards.
* Stay aware of evolving cybercrime trends and real cases.
* One mistake can lose a case — handle evidence carefully.

---

**End of Digital Forensics Student Notes**
