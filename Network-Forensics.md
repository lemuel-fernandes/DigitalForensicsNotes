# Network Forensics

Network forensics is the process of monitoring, capturing, storing, and analyzing network traffic to gather digital evidence. Think of it as a digital detective's work, where the crime scene is the network itself. Investigators look for "footprints" left by attackers, such as malicious packets, unusual traffic patterns, and suspicious network activity.

---

## The OSI Model: The Foundation of Network Communication

To understand network forensics, you first need to grasp the OSI (Open Systems Interconnection) model. Developed by the International Organization for Standardization (ISO), this is a conceptual framework that divides network communication into seven distinct layers.

Each layer has a specific job:

1. **Physical Layer**: This is the hardware layer. It deals with the raw transmission of data as bits over physical media like cables, hubs, and switches.
2. **Data Link Layer**: This layer ensures error-free data transfer between two connected devices (nodes). It's responsible for converting data from upper layers into bits and back again. This layer is split into two sub-layers:
   - **Logical Link Control (LLC)**: Manages flow and error control.
   - **Media Access Control (MAC)**: Provides a unique address for network devices (the MAC address).
3. **Network Layer**: This layer is all about routing. It uses logical addresses (like IP addresses) to ensure data packets reach their correct destination across different networks. Routers operate at this layer.
   - **Key Protocols**: Internet Protocol (IP), Routing Information Protocol (RIP), and Open Shortest Path First (OSPF).
4. **Transport Layer**: This layer is the "traffic cop" of the network. It handles reliable data transfer between end-users, managing flow control, segmentation (breaking data into smaller pieces), and error checking.
   - **Key Protocols**: TCP (Transmission Control Protocol) and UDP (User Datagram Protocol).
   - **TCP Flags**: These are special bits in a TCP packet that indicate the status of a connection. They are crucial for troubleshooting and analysis.
     - **SYN (Synchronize)**: Initiates a connection.
     - **ACK (Acknowledge)**: Confirms receipt of a packet.
     - **FIN (Finish)**: Requests to terminate a connection.
     - **RST (Reset)**: Terminates a connection abruptly.
5. **Session Layer**: This layer creates, manages, and terminates communication sessions between applications. It determines the type of connection: Simplex (one-way), Half-Duplex (two-way, but not at the same time), or Full-Duplex (two-way, simultaneously).
6. **Presentation Layer**: Also known as the "syntax layer," it handles data formatting, compression, and encryption/decryption. It ensures that the data sent by one application is readable by another.
7. **Application Layer**: The top layer, this is the interface users interact with. It provides network services like web browsing (HTTP), file transfers (FTP), and email.

---

## Finding Forensic Footprints

In a network investigation, a "footprint" is any trace an attacker leaves behind. Investigators look for these traces in several places:

- **Packet Capture and Analysis**: Packets are the fundamental units of data in a network. They contain valuable information like source, destination, and content. Analyzing individual packets is essential for determining if traffic is legitimate or from a bot.
- **Network Device Logs**: Most network devices, such as firewalls, routers, and switches, keep detailed logs of all traffic that passes through them. Network log mining is the process of collecting, organizing, and examining these logs to build a timeline of events.
- **Seizure of Network Devices**: Physical networking devices can hold critical data. Investigators follow strict procedures to seize these devices, preserving their contents for forensic analysis. They look for things like traffic allowed/blocked by a firewall, bandwidth usage, and login attempts.
- **Anti-Forensic Techniques**: Cybercriminals often use anti-forensic techniques to hide their tracks. This includes clearing logs, encrypting data, and using IP spoofing. Investigators must be aware of these methods and use specialized tools to overcome them.

---

## Common Network Forensic Artifacts

These are specific types of data that provide valuable evidence:

- **DHCP (Dynamic Host Configuration Protocol) Logs**: These logs show when a computer joined and left a network, and what IP address it was assigned.
- **DNS (Domain Name Server) Traffic**: Analyzing DNS requests and responses helps determine which websites and hosts were contacted.
- **Web Proxy Logs**: These logs capture web traffic requests, responses, and can even contain cached copies of files, including malware.
- **Firewalls, IDS (Intrusion Detection System), and IPS (Intrusion Prevention System) Logs**: These logs provide details about blocked, forwarded, or suspicious traffic, offering crucial leads in an investigation.

---

## Common Network Attacks

Network forensics is often used to investigate and understand various types of attacks:

- **ICMP Attacks**: ICMP (Internet Control Message Protocol) is a protocol used for network diagnostics (like pings). Because it often bypasses firewalls, attackers can misuse it for:
  - **ICMP Sweep Attack**: Scanning a network to find active hosts.
  - **Inverse Mapping Attack**: Mapping internal networks hidden behind a firewall.
  - **ICMP Smurf Attack**: A type of Denial of Service (DoS) attack where an attacker floods a network with ICMP packets, overwhelming the victim.
- **Drive-By Downloads**: This is a client-side attack where a user's system is infected with malware simply by visiting a compromised website. The malicious script works in the background without any user interaction.

---

## Essential Network Forensic Tools

A variety of powerful, open-source tools are available to aid in network forensic investigations:

### Wireshark

Wireshark is a popular network protocol analyzer. It captures and displays network traffic in a detailed, user-friendly interface. It's excellent for:
- **Packet Capture**: Capturing live network traffic.
- **Protocol Analysis**: Inspecting the details of various network protocols.
- **Filtering**: Using powerful display filters to isolate specific packets (e.g., `http.request.method == "GET"`).
- **File Carving**: Extracting files (like executables) from captured network traffic.

**Case Study: File Carving with Wireshark**
1. Open a packet capture file (.pcap) in Wireshark.
2. Filter for relevant requests, like GET requests for HTTP.
3. Right-click on a suspicious packet and select "Follow TCP Stream."
4. If the stream contains an executable file signature (like "MZ"), you can save the file.
5. Use a hex editor to remove any non-file data (like the GET request header) and save the file.
6. Scan the carved file with a tool like VirusTotal to confirm if it's malicious.

### Network Miner

Network Miner is a passive network sniffer that analyzes .pcap files. It automatically extracts and presents key information, such as:
- **Host Details**: IP and MAC addresses, operating systems, and open ports.
- **Files**: Automatically carves out and presents files transmitted over the network.
- **Images**: Extracts images from network traffic.
- **Credentials**: Captures usernames and passwords sent in plain text.
- **DNS Requests**: Lists all DNS requests and responses.
