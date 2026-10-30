## Host-Centric Logs

### Key Host-Centric Log Sources
- **Operating System Logs:** Windows Event Logs, Linux `syslog`, macOS logs. These record events like user logons, process creation, service startups, and failed login attempts.
- **Application Logs:** Logs from software running on the host, such as web servers (Apache, Nginx), databases (MySQL, MSSQL), and other applications.
- **Security Tool Logs:** Logs from antivirus software, Endpoint Detection and Response (EDR) agents, and host-based intrusion detection systems (HIDS).

**Importance of Host-Centric Logs**
- **Detailed Forensic Analysis**
- **Process and Execution Tracking**
- **User Activity Monitoring**
- **Malware Impact Assessment**

![[Pasted image 20260316155716.png]]

## Network-Centric Logs
## Key Network-Centric Log Sources
- **Firewalls:** The firewall logs provide a record of every connection allowed or denied based on pre-defined security rules. Firewall logs are the first place to look for unauthorized connection attempts from the internet.
- **Intrusion Detection/Prevention Systems (IDS/IPS):** They monitor network traffic for patterns that match known malicious attacks (signatures) or for unusual behavior (anomalies). Their logs are critical for detecting active attacks in real time.
- **Routers and Switches:** While not logging in the traditional sense, devices like routers can generate flow data. This data summarizes traffic conversations, telling who talked to whom, for how long, and how much data was sent. It’s excellent for getting a high-level overview of network activity.
- **Web Proxies:** These logs are a goldmine for organizations that route their web traffic through proxies. They record every website user's visit, providing visibility into web-based threats, policy violations, or data exfiltration attempts.
- **VPN:** These devices manage remote access for employees. Their logs track who is connecting to the corporate network, from where, and at what time, which is essential for monitoring the security of remote connections.

**Importance of Network-Centric Logs**
- **Early Threat Detection**
- **Identifying Command & Control (C2)**
- **Tracking Lateral Movement**
- **Detecting Data Exfiltration**
- **Providing Broad Context**

 
![[Pasted image 20260316155730.png]]

## Web-Based Log Sources
- **Web Server Logs:** Apache/Nginx/IIS access and error logs record requests, status codes, user agents and client IPs, useful for spotting scanning, injection attempts and webshell access.
- **WAF and Reverse Proxy Logs:** Record blocked and allowed web requests and the matched rules.

![[Pasted image 20260316155750.png]]

## Windows
[[EventViewer]]
## Linux
[[Log/Linux/General]]
## WebServer
[[Log/Linux/General]]