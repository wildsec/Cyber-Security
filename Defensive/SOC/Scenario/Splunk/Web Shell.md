  
**Alert Details:**

- **Alert Name:** Potential Web Shell Upload Detected
- **Time:** 14/09/2025 09:31:51 AM
- **Resource:** http://web.trywinme.thm
- **Suspicious IP:** 171.251.232.40

Examine the specific activity carried out by this IP address
```
index=web-alert 171.251.232.40  
| table _time clientip useragent uri_path method status   
| sort + _time
```
![[Pasted image 20260317161249.png]]

Exclude Hydra, not looking for brute force -> web shell
```
index=web-alert 171.251.232.40 useragent!="Mozilla/5.0 (Hydra)" 
| table  _time clientip useragent uri_path referer referer_domain method status
```
![[Pasted image 20260317161415.png]]

Let’s now take a closer look at the logs related to b374k.php
```
index=web-alert 171.251.232.40 b374k.php
| table _time clientip useragent uri_path referer referer_domain method status  
| sort + _time
```
![[Pasted image 20260317161602.png]]
## Next Investigation Steps

These questions should be reviewed by the Level 2 analyst:

- Was the brute force attack using successful?
- How did the attacker upload the web shell to the server, given that L1 did not identify any traces of the upload?
- What specific actions did the attacker perform on the server using commands through the web shell?