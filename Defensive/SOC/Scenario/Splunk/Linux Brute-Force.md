  
**Alert Details:**

- **Alert Name:** Brute Force Activity Detection
- **Time:** 17/09/2025 9:00:21 AM
- **Target Host:** tryhackme-2404
- **Source IP:** 10.10.242.248

Tools: Splunk

Query will search for both successful and failed login attempts, as well as events related to invalid users,
``` 
sourcetype="linux_secure" 10.10.242.248
| search "Accepted password for" OR "Failed password for" OR "Invalid user"  
| sort + _time
```

Number of login attempts made for each user
``` 
sourcetype="linux_secure" 10.10.242.248
| rex field=_raw "^\d{4}-\d{2}-\d{2}T[^\s]+\s+(?<log_hostname>\S+)"
| rex field=_raw "sshd\[\d+\]:\s*(?<action>Failed|Accepted)\s+\S+\s+for(?: invalid user)? (?<username>\S+) from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| eval process="sshd"
| stats count values(src_ip) as src_ip values(log_hostname) as hostname values(process) as process by username
```

Determine whether the attacker actually gained access to the system.
``` 
sourcetype="linux_secure" 10.10.242.248
| rex field=_raw "^\d{4}-\d{2}-\d{2}T[^\s]+\s+(?<log_hostname>\S+)"
| rex field=_raw "sshd\[\d+\]:\s*(?<action>Failed|Accepted)\s+\S+\s+for(?: invalid user)? (?<username>\S+) from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| eval process="sshd"
| stats count values(action) values(src_ip) as src_ip values(log_hostname) as hostname values(process) as process  by username
```


## Next Investigation Steps
- Why did the attacker have a local IP address? Could it be that they are already inside our network? If so, for how long?
- How did the attacker obtain information about the users, specifically their usernames?
- What happened after the attacker gained access to the tryhackme-2404 host?