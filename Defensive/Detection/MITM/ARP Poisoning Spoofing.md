[[Defensive/Detection/MITM/General]]
[[ARP]]

Address Resolution Protocol Poisoning (also known as ARP Spoofing or Man In The Middle (MITM) attack) is a type of attack that involves network jamming/manipulating by sending malicious ARP packets to the default gateway. The ultimate aim is to manipulate the**"IP to MAC address table"**and sniff the traffic of the target host.

## Indicators of the Attack
- **Duplicate MAC-to-IP Mappings**: Multiple MAC addresses claiming the same IP address. Indicates impersonation.
- **Unsolicited ARP Replies**: High number of ARP replies without matching requests ("gratuitous ARP").
- **Abnormal ARP Traffic Volume:** A Large number of ARP packets in short intervals.
- **Unusual Traffic Routing**: Traffic rerouted through the attacker’s MAC.
- **Gateway Redirection Patterns:** Multiple destination MACs for the same gateway IP.
- **ARP Probe / Reply Loops**: Many ARP requests with `Who has 192.168.1.x? Tell 192.168.1.y` patterns.
 
## Wireshark  [[Network/Tools/Wireshark/General|General]]

| **Notes**                               | **Wireshark filter**                                                                                                                                                                              |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Global search                           | `arp`                                                                                                                                                                                             |
| ARP requests.                           | `arp.opcode == 1`                                                                                                                                                                                 |
| ARP responses.                          | `arp.opcode == 2`                                                                                                                                                                                 |
| Arp scanning                            | `arp.dst.hw_mac==00:00:00:00:00:00`                                                                                                                                                               |
| Possible ARP poisonin                   | `arp.duplicate-address-detected or arp.duplicate-address-frame`                                                                                                                                   |
| Possible ARP flooding from              | `((arp) && (arp.opcode == 1)) && (arp.src.hw_mac == target-mac-address)`                                                                                                                          |
| unsolicited (gratuitous) ARP replies    | `arp.isgratuitous`                                                                                                                                                                                |
| ARP traffic associated with the Gateway | `arp && arp.src.proto_ipv4 == 192.168.10.1 && eth.src == 02:aa:bb:cc:00:01`<br>`arp.opcode == 2 && arp.src.proto_ipv4 == 192.168.10.1`<br>`arp.opcode == 2 && arp.src.proto_ipv4 == 192.168.10.1` |
|                                         |                                                                                                                                                                                                   |
