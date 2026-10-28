The term **kill chain** is a military concept related to the structure of an attack. It consists of target identification, decision and order to attack the target, and finally the target destruction.

## Reconnaissance
[[Reconnaissance]]

## Weaponization

After a successful reconnaissance stage, "Megatron" would work on turning the raw information into actionable attack tools through crafting **malware** and **exploits** into a **payload**.

## Delivery

## Exploitation
Exploitation is the moment the attacker's code executes on the target, taking advantage of a known vulnerability.

## Installation
Once the attacker gets access to the system, he would want to reconnect back to the system if he loses the connection to it or if he got detected and got the initial access removed. Or if the system is later patched, they will no longer have access to it. That is when the attacker needs to install a **[persistent backdoor](https://www.offensive-security.com/metasploit-unleashed/persistent-backdoors/).** A persistent backdoor will let the attacker access the system he compromised in the past.

How:
* webshell
* meterpreter
* MITRE ATT&CK
* Startup run key

## Command & Control
This term is also known as **C&C or C2 Beaconing** as a type of malicious communication between a C&C server and malware on the infected host. The infected host will consistently communicate with the C2 server; that is also where the beaconing term came from.

The most common C2 channels used by adversaries include:

- HTTP on port 80 and HTTPS on port 443, where this type of beaconing blends the malicious traffic with the legitimate traffic and can help the attacker evade firewalls.
    
- DNS (Domain Name Server), where the infected machine makes constant DNS requests to the DNS server that belongs to an attacker, this type of C2 communication is also known as DNS Tunneling

## Exfiltration
With hands-on keyboard access, the attacker can achieve the following: 

- Collect the credentials from users.
- Perform privilege escalation (gaining elevated access like domain administrator access from a workstation by exploiting the misconfiguration).
- Internal reconnaissance (for example, an attacker gets to interact with internal software to find its vulnerabilities).
- Lateral movement through the company's environment.
- Collect and exfiltrate sensitive data.
- Deleting the backups and shadow copies. Shadow Copy is a Microsoft technology that can create backup copies, snapshots of computer files, or volumes. 
- Overwrite or corrupt data.