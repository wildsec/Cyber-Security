### Trust But Verify (Traditional Model)  
  
| Aspect | Description |  
|--------|-------------|  
| **Philosophy** | Establish trust first, then verify occasionally |  
| **Approach** | "Inside the perimeter = trusted; outside = untrusted" |  
| **Verification** | One-time authentication, then implicit trust |  
| **Typical Model** | Castle-and-moat: Strong perimeter, soft interior |  
| **Example** | VPN login → full network access; logged-in user → access all allowed resources |  
  
---  
  
### Zero Trust (Modern Model)  
-> is essentially [[ISO IEC 19249]] principles applied at enterprise scale
  
| Aspect | Description |  
|--------|-------------|  
| **Philosophy** | **"Never trust, always verify"** |  
| **Approach** | **No implicit trust anywhere** — verify every request, every time |  
| **Verification** | Continuous, context-aware authentication & authorization |  
| **Typical Model** | Perimeter-less; trust evaluated per transaction |  
| **Example** | Each API call re-verified; device health checked continuously; micro-segmentation |

---  
  
## Key Differences  
  
| Trust But Verify | Zero Trust |  
|------------------|------------|  
| Trust based on **location/network** | Trust based on **identity + context** |  
| **Perimeter-focused** | **Identity-focused** |  
| Verify **once** (at entry) | Verify **continuously** |  
| Assumes internal traffic is safe | Assumes breach already happened |  
| "Verify" = audit/spot-check | "Verify" = real-time policy enforcement |  
| Broad access after authentication | Least-privilege, granular access |  
  
---  
  
## Real-World Analogy  
  
| Scenario | Trust But Verify | Zero Trust |  
|----------|------------------|------------|  
| **Airport** | Check ID at entrance → free roam | Check ID at every gate + bag check |  
| **Office** | Badge in at lobby → access everything | Badge + biometrics per room + device posture check |  
| **Banking** | Login once → full account access | Re-authenticate for transfers, new device = blocked |  
  
---  
  
## Why Zero Trust Won  
  
| Attack | Trust But Verify Fails | Zero Trust Responds |  
|--------|------------------------|---------------------|  
| Lateral movement after breach | ![✅](https://web.telegram.org/a/img-apple-64/2705.png) Easy (inside = trusted) | ![❌](https://web.telegram.org/a/img-apple-64/274c.png) Blocked (verify every hop) |  
| Compromised credentials | ![✅](https://web.telegram.org/a/img-apple-64/2705.png) Full access granted | ![❌](https://web.telegram.org/a/img-apple-64/274c.png) Context anomaly detected |  
| Insider threat | ![✅](https://web.telegram.org/a/img-apple-64/2705.png) Implicit trust abused | ![❌](https://web.telegram.org/a/img-apple-64/274c.png) Behavior analytics catch it |  
| Cloud/mobile work | ![❌](https://web.telegram.org/a/img-apple-64/274c.png) Perimeter doesn't exist | ![✅](https://web.telegram.org/a/img-apple-64/2705.png) Designed for distributed |  
  
---  
  
## Bottom Line  
  
| Model | Era | Best For |  
|-------|-----|----------|  
| **Trust But Verify** | 1990s-2010s | On-prem, fixed perimeters, legacy systems |  
| **Zero Trust** | 2020s+ | Cloud, hybrid, remote work, OT/IT convergence |