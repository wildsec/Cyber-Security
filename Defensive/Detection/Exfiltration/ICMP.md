[[General Protocols]]
## How adversaries use ICMP for exfiltration

Common techniques:

- ICMP echo (type 8) / reply (type 0) tunneling: attackers place encoded (base64, hex) chunks of files inside ICMP payloads. The remote server collects and decodes them.
- Custom ICMP types/codes: using uncommon ICMP types or non-zero codes to avoid signature-based detections.
- Fragmentation and reassembly: large payloads are split across multiple packets.
- Encryption/obfuscation: Encrypting or encrypting payloads (base64 is common) to look like random data.

Indicators that something may be malicious:

- Persistent ICMP sessions to an external host not used for legitimate monitoring.
- Unusually large ICMP payloads or frequent ICMP with payload > typical ping size.
- ICMP payloads that contain high-entropy data or patterns consistent with base64/hex.
- Bursts of ICMP are immediately followed by no other legitimate application traffic from the same host.
## Wireshark
`icmp.type == 8`
`icmp.type == 8 and frame.len > 100`

Normal pings are ~74 bytes total.