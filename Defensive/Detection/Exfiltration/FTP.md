[[General Protocols]]
Detection relies on a mix of packet inspection (FTP only), server logs, SSH session metadata, and network flow/size/pattern analysis.

## How adversaries use FTP for exfiltration
- Use **legitimate FTP servers** (public or misconfigured internal servers) to stage/transfer data.
- Use **compromised credentials** (service accounts, user creds).
- Use **non-standard ports** or tunneling to blend with other traffic.
## Indicators of attack
- `USER` and `PASS` commands (cleartext credentials).
- `STOR` (upload) and `RETR` (download) commands: repeated or large transfers.
- Large data connections to unusual external IPs, especially outside business hours.
- Data channel openings on ephemeral ports (PASV) paired with large payloads.

## Wireshark
`ftp || ftp-data`
`ftp.request.command == "USER" || ftp.request.command == "PASS"`
`ftp contains "STOR"` Right-click a `packet → Follow → TCP Stream`
`ftp contains "csv"`
`ftp && frame.len > 90`