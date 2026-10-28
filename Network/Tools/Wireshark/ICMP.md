[[General Protocols]]
Internet Control Message Protocol (ICMP) is designed for diagnosing and reporting network communication issues. It is highly used in error reporting and testing. As it is a trusted network layer protocol, sometimes it is used for denial of service (DoS) attacks; also, adversaries use it in data exfiltration and C2 tunnelling activities.

| **Notes**                                                                                                                                                          | **Wireshark filters**      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------- |
| Global search                                                                                                                                                      | - `icmp`                   |
| **"ICMP" options for grabbing the low-hanging fruits:**<br><br>- Packet length.<br>- ICMP destination addresses.<br>- Encapsulated protocol signs in ICMP payload. | - `data.len > 64 and icmp` |
![[Pasted image 20260309130218.png]]