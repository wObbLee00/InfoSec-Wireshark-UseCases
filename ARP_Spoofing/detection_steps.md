⚠️ Use Case 3: ARP Spoofing Detection

🎯 Objective
To detect ARP spoofing using MAC-IP mismatch analysis in Wireshark.

🧪 Steps Followed

1️⃣ Capture ARP Packets in Wireshark
<img width="960" height="539" alt="image" src="https://github.com/user-attachments/assets/008a6ba8-c9d6-4e5a-9336-0b132e2cbe81" />
2️⃣ Apply ARP filter: arp
<img width="952" height="535" alt="image" src="https://github.com/user-attachments/assets/da5499e8-3b98-4bcc-b8c1-d226cecbb05c" />
Use specific filter: arp.opcode == 1 to isolate ARP broadcasts.

<img width="952" height="535" alt="image" src="https://github.com/user-attachments/assets/65d507c4-7c96-4659-9091-6750a279f59a" />
Use specific filter: arp.opcode == 2 to isolate ARP replies.

<img width="952" height="535" alt="image" src="https://github.com/user-attachments/assets/a3dd6cb1-1c48-4844-8a4a-d1632e426a96" />
3️⃣ Analyze MAC-to-IP Mappings

Check for inconsistent MAC addresses assigned to a single IP address.

<img width="944" height="531" alt="image" src="https://github.com/user-attachments/assets/2ee029ae-bb06-4f35-862c-898b340a79ad" />

✅ Outcome
Detected ARP spoofing activity by tracking inconsistent MAC-IP bindings and identifying malicious "gratuitous" replies.

🧰 Tools Used
Wireshark

ARP spoofing simulation (optional): arpspoof / ettercap / test attacker VM

Local network or virtual lab

🧠 Insight
ARP spoofing compromises LAN trust. By impersonating a gateway or another host, an attacker can perform Man-in-the-Middle (MITM) attacks, redirect traffic, or hijack sessions.
