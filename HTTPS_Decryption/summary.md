🔐 Use Case 2: HTTPS Header and Payload Decryption

🎯 Objective
To decrypt HTTPS traffic using session key logging and inspect both headers and payloads in Wireshark.


🧪 Steps Followed
1️⃣ Start Wireshark and Capture Traffic
Open Wireshark and begin packet capture.

Visit: https://the-internet.herokuapp.com/login

Perform a login attempt to generate HTTPS POST traffic.
 <img width="900" height="506" alt="image" src="https://github.com/user-attachments/assets/0508311d-3b77-4803-9b58-ffb6aa4cafde" />
 <img width="900" height="506" alt="image" src="https://github.com/user-attachments/assets/15f1e669-fb1b-4c1e-980f-12944f5ef0ef" />

 
2️⃣ Apply Filters to Identify Encrypted Data
   
  Try TLS and HTTP filters on Wireshark to read encrypted data.
  <img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/6c8e2ecb-681f-4c05-afd5-9b44ea848af0" />
  <img width="967" height="543" alt="image" src="https://github.com/user-attachments/assets/2d5b6ed8-73c3-4907-949a-8843f96e4360" />



  Use the filter http.request.method == "POST" 
 <img width="951" height="534" alt="image" src="https://github.com/user-attachments/assets/257cda19-16dd-4509-af3d-511dbe95c6f6" />

3️⃣ Enable SSL Key Logging in Browser
 <img width="651" height="626" alt="image" src="https://github.com/user-attachments/assets/4885cb67-8d8b-4861-940b-d6a35a0ff869" />
 <img width="900" height="848" alt="image" src="https://github.com/user-attachments/assets/fba25196-7d10-45ef-8872-6d8fdc417810" />
 <img width="900" height="228" alt="image" src="https://github.com/user-attachments/assets/d45283ce-85e9-4a4a-b88d-fe4ee1f77ae5" />

 
 
4️⃣ Load SSL Keys in Wireshark
Go to Edit → Preferences → Protocols → TLS

Set the field (Pre)-Master-Secret log filename to the path of your sslkeys.log
<img width="900" height="721" alt="image" src="https://github.com/user-attachments/assets/00638701-58a7-4c8a-9a52-d030e73c030b" />

 

5️⃣ Re-Apply Filters and Inspect Decrypted Traffic
 <img width="900" height="506" alt="image" src="https://github.com/user-attachments/assets/81d76826-672a-46a7-8962-d90d8781bbd8" />

 <img width="949" height="534" alt="image" src="https://github.com/user-attachments/assets/952a62b9-0fce-4f01-887d-a1204bf55b72" />

✅ Outcome
Successfully decrypted HTTPS POST traffic using session key logging. This allowed full inspection of encrypted content using Wireshark, demonstrating how attackers (with access to key material) could potentially eavesdrop.

🧰 Tools Used
Wireshark

Chrome with SSLKEYLOGFILE

The Internet Heroku Demo Website

Environment Variable for TLS key logging

🔒 Note
This technique is only for authorized analysis in test environments. It highlights how HTTPS traffic can be decrypted if key material is exposed, reinforcing the need for secure handling of session keys.
