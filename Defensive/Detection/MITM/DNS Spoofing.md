[[Network/Tools/Wireshark/DNS|DNS]]
[[Network/DNS|DNS]]

**DNS Spoofing** (or DNS Cache Poisoning) is when an attacker corrupts this system. They give your computer the wrong "phone number" for a website you're trying to visit.
![[Pasted image 20260311093015.png]]

## Indicators of the Attack
- **Multiple DNS responses for the same query**: A legitimate resolver and a forged responder reply to the same query. This is the single most reliable indicator.
- **DNS response from an unexpected source**: A DNS reply arrives from an IP address **that does not match any configured resolver** (like 8.8.8.8 or your DNS server).
- **Suspiciously short TTL (Time-To-Live) values**: Attackers use very low TTLs (1 - 30s) to keep poisoned entries short-lived and reassert control.
- **Unsolicited DNS responses**: A DNS reply appears without a corresponding DNS request from the victim.

| **Notes**                     | **Wireshark Filter**                                                                           |
| ----------------------------- | ---------------------------------------------------------------------------------------------- |
| Global search                 | `dns`                                                                                          |
| Filter legit                  | `dns.flags.response == 1 && ip.src == 8.8.8.8`                                                 |
| Responses                     | `dns.flags.response==1`                                                                        |
| filter for domain             | `dns.flags.response == 1 and ip.src != 8.8.8.8`                                                |
| from dns server filter domain | `dns.flags.response == 1 && ip.src == 8.8.8.8 && dns.qry.name == "corp-login.acme-corp.local"` |
| NOT from dns server           | `dns.flags.response == 1 && ip.src != 8.8.8.8 && dns.qry.name == "corp-login.acme-corp.local"` |
|                               |                                                                                                |
