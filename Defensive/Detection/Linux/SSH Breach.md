[[Authentication]]
## Indicators
![[Pasted image 20260315093313.png]]

## Detecting SSH Attacks
- Password-based authentication,
- logins from external IPs
- time difference between the logins (logins must be at night for the user,?)

- **Username**: Who owns the user? Is it expected for them to log in at this time and from this IP?
- **Source IP**: What do [TI tools](https://tryhackme.com/room/ipanddomainthreatintel) and [asset lookups](https://tryhackme.com/room/socworkbookslookups) say about the IP? Is it trusted or malicious?
- **Login history**: Was the login preceded by brute force or other suspicious system events?
- **Next steps**: Is the login suspicious? Should I analyze user actions following the login?