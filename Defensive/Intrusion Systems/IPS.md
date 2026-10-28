# IPS

**Intrusion Prevention System**

IPS is an active protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for stopping/preventing/terminating the suspicious event as soon as it is detected.

## Types
- **Network Intrusion Prevention System (NIPS)**: NIPS monitors the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If a signature is identified, the connection is terminated.
- **Behaviour-based Intrusion Prevention System (Network Behaviour Analysis - NBA)**: Behaviour-based systems monitor the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If an anomaly is identified, the connection is terminated.
- **Wireless Intrusion Prevention System (WIPS)**: WIPS monitors the traffic flow from a wireless network. Its aim is to protect wireless traffic and stop possible attacks launched from there. If a signature is identified, the connection is terminated.
- **Host-based Intrusion Prevention System (HIPS)**: HIPS actively protects the traffic flow from a single endpoint device. The aim is to investigate the traffic on a particular device. If a signature is identified, the connection is terminated.

The Network Behaviour Analysis System works similar to NIPS. The difference between NIPS and Behaviour-based systems is that behaviour-based systems require a training period (also known as "baselining") to learn the normal traffic and differentiate the malicious traffic and threats. This model provides more efficient results against new and unknown threats.

## Related Topics
- [IDS](IDS.md) - Intrusion Detection System
- [Firewall](../../Firewall/Types.md) - Firewall technologies
- [Blue Team](../Blue%20Team.md) - Defensive security team
