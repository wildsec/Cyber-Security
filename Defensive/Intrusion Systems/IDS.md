# IDS

**Intrusion Detection System**

The IDS plays the role of surveillance cameras. It sits in a corner, monitors the network traffic based on its signature and anomaly-based detections, and detects any abnormal traffic going out or inside the network.

## Deployment Modes
- **Host Intrusion Detection System (HIDS):** Host-based IDS solutions are installed individually on the hosts and are responsible for only detecting potential security threats associated with that particular host.
- **Network Intrusion Detection System (NIDS):** Network-based IDS solutions are crucial in detecting potentially malicious activities within the whole network, regardless of any specific host. 
![[Pasted image 20260310180514.png]]

## Detection Modes
- **Signature-Based IDS:** Each attack has its unique pattern, which is known as a signature. These signatures are preserved by the IDS in their databases so that if the same attack happens in the future, it gets detected by its signature and reported to the security administrators for action. 
- **Anomaly-Based IDS:** This type of IDS first learns the normal behavior (baseline) of the network or system and performs detections if there is any deviation from the normal behavior. Anomaly-based IDS can also detect zero-day attacks because they don't rely on available signatures for detection. 
- **Hybrid IDS:** A hybrid IDS combines the detection methods of signature-based IDS and anomaly-based IDS to leverage the strengths of each approach. 

## Tools
- [Snort](Tools/Snort/General.md) - Open source IDS/IPS

## Related Topics
- [IPS](IPS.md) - Intrusion Prevention System
- [Blue Team](../Blue%20Team.md) - Defensive security team
- [SOC](../SOC/General.md) - Security Operations Center
