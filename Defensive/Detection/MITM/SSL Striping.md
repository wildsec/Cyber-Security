[[HTTP(S)]]
[[HTTPS]]

SSL stripping is a man-in-the-middle technique in which an attacker intercepts and modifies traffic to remove or prevent TLS encryption between a client and a server. This causes the client to communicate over HTTP instead of HTTPS. The attacker retains a secure (HTTPS) session with the server while relaying plain HTTP to the victim, enabling eavesdropping and credential capture.

## How It Works

1. **The victim initiates an HTTPS request** to a website.
2. **The attacker intercepts the request** using ARP spoofing or a rogue access point.
3. **The attacker connects to the website over HTTPS** but relays the response to the victim through HTTP.
4. **The victim unknowingly interacts over HTTP**, exposing sensitive data in plaintext.
## Indicators of SSL stripping

- **Initial Request vs. Response:** The user's initial request may be for `HTTPS` (port 443), but the subsequent packets immediately shift to unencrypted `HTTP` (port 80) for the same domain.
- **Redirects/Link Rewriting**: Monitoring for redirects (HTTP Status Codes 301, 302) that persistently direct an HTTPS request to an HTTP resource.
- **Certificate Errors**: Although the attacker usually tries to hide this, the initial **TLS/SSL Handshake** may fail or display a self-signed certificate if the attacker uses a more direct proxying technique.


| **Notes**                                                         | **Wireshark Filter**                                                                              |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| SSL traffic                                                       | `tls \|\| ssl`                                                                                    |
| established TLS handshakes to our server (is domain ssl normally) | `tls.handshake.type == 1 && tls.handshake.extensions_server_name == "corp-login.acme-corp.local"` |
| check IPs if ssl dissapeared                                      | `http && ip.src == 192.168.10.10 && ip.dst == 192.168.10.55`                                      |
|                                                                   |                                                                                                   |
