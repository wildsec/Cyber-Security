**MITM** Man-in-the-Middle is a cyberattack where an attacker secretly intercepts and potentially alters communication between two parties, such as a user and a service, without their knowledge.

![[Pasted image 20260311090821.png]]

- **Interception**: The attacker inserts themselves into a communication stream, often by exploiting weaknesses in network protocols or by using techniques like [[ARP Poisoning Spoofing]], [[Network/Tools/Wireshark/DNS|DNS]], or IP spoofing.
- **Manipulation/Decryption**: The attacker tries to access or modify the communication, decrypting encoded data or injecting harmful content, such as altered website responses or fake login forms.

## Common Types of MITM Attacks
- Packet sniffing: Capturing unencrypted data packets exchanged over a network, often on open Wi-Fi.
- Session hijacking: Stealing and using session tokens to impersonate users.
- [[SSL Striping]]: Downgrading HTTPS connections to insecure HTTP to steal or alter data transferred.
- [[DNS Spoofing]]: Redirecting legitimate website traffic to fraudulent domains by manipulating DNS responses.
- IP spoofing: Crafting malicious IP packets that appear to come from trusted systems.
- Rogue Wi-Fi access point: Creating fake networks to intercept user traffic.
## MITM and Cyber Kill Chain
- **As an Exploitation Technique:** A MITM attack exploits the inherent trust and design limitations of core network protocols like ARP and DNS. By manipulating these protocols, an attacker can intercept a communication channel. This act of session interception is a form of exploitation, as it violates the integrity of the network and provides the adversary with their initial foothold for eavesdropping or active manipulation.
- **As an Installation Vector:** Once an attacker has successfully established a MITM position, they control the data stream and can use it as a delivery mechanism for malicious payloads. For example, an attacker can inject a browser exploit, a malware dropper, or a remote access trojan (RAT) into legitimate, unencrypted downloads. This action corresponds to the Installation phase, where the adversary establishes persistence or deploys additional malicious tools onto the victim's system.
## Summary
- **[[ARP Poisoning Spoofing]] (cache poisoning):**
    - **ARP spoof begins**, attacker sends unsolicited ARP `is-at` claiming gateway IP.
- **[[DNS Spoofing]] (forged DNS responses):**
    - **Victim DNS query** for `corp-login.acme-corp.local`.
    - **Forged DNS response** from attacker, answers domain → `192.168.10.55`.
- **[[SSL Striping]] (TLS downgrade / credential capture):**
    - **The Victim initiates connection** to resolved IP, HTTP to attacker (SSL stripping effect).
    - **Credential POST observed** (cleartext).