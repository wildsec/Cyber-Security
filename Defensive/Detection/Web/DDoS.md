**Denial-of-Service**
At their core, **Denial-of-Service (DoS)** attacks are meant to overwhelm a website or app so that people can’t use it. When this happens, customers can’t log in, shop, or access services, and businesses lose money and trust.
![[Pasted image 20260312165035.png]]

## Distributed DoS (DDoS)

![[Pasted image 20260312165041.png]]

|DoS Attack Type|Description|
|---|---|
|Slowloris|Sending many partial HTTP requests to tie up server resources|
|HTTP Flood|Sending a large number of HTTP requests to overwhelm the server|
|Cache Bypass|Bypassing CDN edge servers and forcing the origin server to respond|
|Oversized Query|Forcing the server to process large, resource-intensive requests|
|Login/Form Abuse|Overloading authentication logic with login attempts or password resets|
|Faulty Input Validation Abuse|Exploiting poorly designed input handling|

**Possible Attack Motives**

|Motive|Description|Example Scenario|
|---|---|---|
|[Financial Loss](https://www.curotec.com/insights/christmas-hackers-attacks-increase-around-holidays/)|Disrupt services to stop or reduce sales and revenue|Flooding an e-commerce website during peak holiday sales|
|[Extortion](https://www.cloudflare.com/learning/ddos/ransom-ddos-attack/)|Demand payment to stop a current attack|Threatening a bank with a ransom DDoS|
|[Hacktivism](https://www.zayo.com/resources/how-governments-can-combat-ddos-risk-during-elections/)|Disruption for social or political protest|Attacking government websites during election season|
|[Distraction](https://www.cyberdefensemagazine.com/ddos-as-a-distraction/)|Redirect defenders' attention while other attacks take place|Launching a DDoS while attacking other infrastructure|
|[Competition](https://digitalmarketingdesk.co.uk/63-of-ddos-attacks-linked-to-competitors/)|Disrupt a rival's service to drive up their costs or gain market share|A competitor launches a DDoS during a product launch|
|[Denial of Wallet](https://blog.limbus-medtec.com/the-aws-s3-denial-of-wallet-amplification-attack-bc5a97cc041d)|Force the victim to rack up service usage costs|Attackers repeatedly access AWS S3 data, generating costs per request|
|[Reputational Damage](https://stormwall.network/resources/blog/how-ddos-attacks-are-hurting-esports)|Cause customers to lose trust in a company|Game servers crashing during launch day|

## Detection
|Indicator|Example|Description|
|---|---|---|
|High Request Rate|`10.10.10.100` → 1000 `GET /login`|A resource-heavy page like `/login` is flooded with requests to overwhelm authentication processes. Login pages are common targets since each request may trigger password checks and database queries|
|Odd User-Agents|`curl/7.6.88` → `/index` repeatedly|Attackers spoof outdated or unusual User-Agents to blend in or bypass filters. Spotting traffic with tools like `curl` or `Python-urllib/3.x`, for example, can be a red flag for automated attacks|
|Geographic Anomalies|IP address origins dotted around the world|Legitimate traffic typically comes from a few regions where real users are located. A globally distributed botnet may utilize IP addresses from around the world|
|Burst Timestamps|50 requests in 1 second → `/search`|A sudden spike of requests packed into the same second creates an unnatural traffic pattern that points to automation|
|Server Errors ([5xx](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status#server_error_responses))|A significant spike of `503 Service Unavailable` errors|A sudden surge of server error responses (`500` - `511`) indicates resources are maxed out and the service is struggling under attack traffic|
|Logic Abuse|`GET /products?limit=999999`|Attackers craft queries that overload the server, forcing it to load huge amounts of information and slowing it down for everyone|

## Log Sample

Let's examine a sample condensed access log to see how a DoS attack might appear in a post-incident scenario. 

1. **Normal User Traffic** - Every few seconds, a user requests a page and receives a response as expected
2. **DoS Attack** - Beginning at `10:01:10`, you can see the IP address `203.0.113.55` begin to send repeated `GET` requests to `/login.php`
3. **Web Server Down** - Users are requesting pages and receiving `503` responses indicating the service is unavailable

![[Pasted image 20260312165412.png]]

