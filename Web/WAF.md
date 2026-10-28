Web Application Firewall

**WAFs** are a powerful tool that can be integrated as another layer of protection for websites and web applications. They inspect incoming HTTP traffic and block or log potentially harmful requests based on security rules.

- Cloud-based (**Reverse Proxy**): Sits in front of the web server. These WAFs are easy to deploy and have great scalability.
- Host-based: Software deployed directly on the web server and offers control for each application.
- Network-based: A physical or virtual appliance situated on the network perimeter. More suited for enterprise environments.

|WAF Feature|Detection Method|Example|
|---|---|---|
|Signature-Based Detection|Matches known attack patterns or payloads|A request with a User-Agent that matches a known tool, `sqlmap/1.8.1`|
|Heuristic-Based Detection|Analyzes the context and behavior of requests|A long query string with special characters `search?q=%3Cscript%20(1)`|
|Anomaly & Behavioral Analysis|Flags deviations from normal traffic behavior|A single IP address makes repeated login attempts in a short period of time|
|Location & IP Reputation Filtering|Uses location and threat intel to block IPs|A request from an IP address that is outside of your normal business area|

## Rules

WAFs inspect and decide whether to allow a web request or block it entirely based on predefined rules. Let's examine a few categories of firewall rules.

|Rule Type|Description|Example Use Case|
|---|---|---|
|Block common attack patterns|Blocks known malicious payloads and indicators|Block malicious User-Agents: `sqlmap`|
|Deny known malicious sources|Uses IP reputation, threat intel, or geo-blocking to stop risky traffic|Block IPs from recent botnet campaigns|
|Custom-built rules|Tailored to your specific application’s needs|Allow only GET/POST requests to `/login`|
|Rate-limiting & abuse prevention|Limits request frequency to prevent abuse|Limit login attempts to 5 per minute per IP|