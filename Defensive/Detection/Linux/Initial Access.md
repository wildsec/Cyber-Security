# Initial Access Detection

Detecting initial access attempts is critical for early threat detection.

![[Pasted image 20260315094832.png]]

## Common Initial Access Vectors

### External Facing Services
- VPN endpoints
- Remote Desktop (RDP) services
- Web applications
- Email gateways
- SSH services

### Detection Opportunities
- Unusual login times or locations
- Failed authentication attempts followed by success
- New user accounts created
- Service account usage anomalies
- Exploit attempts in web server logs

## Related Topics
- [Authentication](Authentication.md) - Authentication-related detection
- [Privilege Escalation](Privilege%20Escalation.md) - Post-access elevation
- [Persistence](Persistence.md) - Maintaining access
- [MITRE ATT&CK - Initial Access](https://attack.mitre.org/tactics/TA0001/)
