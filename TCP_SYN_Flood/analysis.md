🌐 Use Case 1: TCP SYN Flood Detection

🎯 Objective
To detect signs of a TCP SYN flood attack using Wireshark by analyzing incomplete TCP handshakes.

🧪 Steps Followed

1️⃣ Host a website locally using XAMPP.
<img width="981" height="703" alt="image" src="https://github.com/user-attachments/assets/f71560ca-fc8d-4fd3-95e5-641664ca9407" />
<img width="979" height="737" alt="image" src="https://github.com/user-attachments/assets/c611044c-1ef4-4b3b-a5e2-07fa0b86f41a" />
2️⃣ Open Wireshark and Start Packet Capture
Both Loopback and Wi-Fi interfaces as this attack was done from and on the same device.
<img width="987" height="555" alt="image" src="https://github.com/user-attachments/assets/fb0fa088-9703-4d46-92c2-57b50827c0bd" />
<img width="991" height="557" alt="image" src="https://github.com/user-attachments/assets/07d8c907-0c65-4f24-b2c5-d2c42117a5f2" />
3️⃣ Simulate Traffic with SYN Flood Behavior
Used a controlled lab environment or simulated packets using tools like Scapy or a test machine.

Sent a large number of SYN packets to a server IP without completing the 3-way handshake.
<img width="995" height="560" alt="image" src="https://github.com/user-attachments/assets/7b600ad9-3bfd-4d60-864d-5d85b655ad1f" />
<img width="900" height="506" alt="image" src="https://github.com/user-attachments/assets/fe8d8961-97b8-4a4f-b066-203e69004437" />
4️⃣  Identify Suspicious Behavior
Notice unusual patterns:

Multiple SYNs from different or spoofed IPs.

Server not responding or overwhelmed.

TCP conversations show no full handshakes (SYN → SYN-ACK → ACK).
<img width="948" height="533" alt="image" src="https://github.com/user-attachments/assets/e5f3f7b6-8847-4e20-be7e-7f19e8b0d53d" />
<img width="944" height="531" alt="image" src="https://github.com/user-attachments/assets/5d5ff564-3362-49ed-ad39-0acde5842e0c" />
All SYN packets 
tcp.flags.syn == 1 && tcp.flags.ack == 0
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/6ab12f62-ddc2-432a-ad32-67a88f86618d" />
All SYN packets from the source “10.0.0”
ip.src >= 10.0.0.1 && ip.src <= 10.0.0.255 && tcp.flags.syn == 1 && tcp.flags.ack == 0
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/1587eac3-f4db-4a4b-b093-57b789e90d3d" />
All SYN and ACK packets sent to the destination “10.0.0”
ip.dst >= 10.0.0.1 && ip.dst <= 10.0.0.255 && tcp.flags.syn == 1 && tcp.flags.ack == 1
<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/8fd128b2-a12a-4bdd-964b-d3e819b78b98" />
All ACK sent by the source “10.0.0”
ip.src >= 10.0.0.1 && ip.src <= 10.0.0.255 && tcp.flags.syn ==0 && tcp.flags.ack==1
<img width="928" height="522" alt="image" src="https://github.com/user-attachments/assets/7671bad8-8c4b-495d-bc7c-81bc03a099d2" />
✅ Outcome
SYN flood attack was successfully identified by observing numerous unacknowledged SYN packets — classic DoS behavior.

🧰 Tools Used
Wireshark

Optional: Scapy, hping3 or similar tools for traffic simulation

Local network or virtual lab
