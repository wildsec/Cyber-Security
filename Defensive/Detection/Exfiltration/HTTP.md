[[HTTP(S)]]

## How adversaries use HTTP for data exfiltration

- **POST uploads to external servers**: Bulk data is sent to attacker-controlled hosts or cloud storage in POST request bodies.
- **GET requests with encoded data**: Attacker squeezes small chunks into query strings or path segments (useful for low-and-slow exfiltration).
- **Use of common services / CDN**: Exfiltration disguised as uploads to popular services or attacker-controlled subdomains under reputable domains.
- **Custom headers**: Data placed in headers (e.g., `X-Data: <base64>`) may bypass some string-based DLP.
- **Chunked transfer / multipart**: Large payloads split into multiple requests to avoid size thresholds.
- **HTTPS/TLS tunneling**: The encrypted channel hides the payload; detection requires TLS inspection, SNI analysis, or metadata-based detection.
- **Staging via cloud services**: The attacker uploads to Dropbox/GitHub/Gist and then fetches externally.
### Common network indicators

- Unusually large HTTP POST requests to external/unexpected hosts.
- HTTP requests to domains with low reputation / rarely seen in baseline traffic.
- Frequent small requests (beaconing) to the same host, followed by large uploads.
- Chunked or multipart transfers where multiple requests compose a larger file.

## Splunk
`method=POST | stats count avg(bytes_sent) max(bytes_sent) min(bytes_sent) by domain | sort - count`
`bytes_sent > 600 | table _time src_ip uri domain dst_ip bytes_sent | sort - bytes_sent`

## Wireshark
