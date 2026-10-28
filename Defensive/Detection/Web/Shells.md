Detecting WebShells
![[Pasted image 20260312162444.png]]
A web shell is a malicious program uploaded to a target web server, enabling adversaries to execute commands remotely. Web shells often serve as both an [initial access](https://attack.mitre.org/techniques/T1190/) method (via file upload vulnerabilities) and a [persistence](https://attack.mitre.org/techniques/T1505/003/) mechanism.

**Legitimate Function Abuse**  
Web shells rely on the abuse of legitimate functions within programs.  
System execution functions in PHP, such as `shell_exec()`, `exec()`, `system()`, and `passthru()`, can be abused to gain command execution.

![[Pasted image 20260312162930.png]]
## File System Analysis
It should be noted that some platforms like WordPress and Django store page content in a database rather than a file system, so malicious code may be injected into posts, themes, or settings and won't appear in normal file system searches.
Common web server directories where web shells are typically placed:
- Apache: `/var/www/html/` Default on most Linux distros
- Nginx: `/usr/share/nginx/html/` Default on many Linux setups

**Suspicious or Random File Names**  
Can be used by attackers to evade detection. Be on the lookout for names that deviate from standard application files. 

- Monitor files with executable extensions like `.php` & `.jsp`
- Be on the lookout for double extensions to disguise malicious files `image.jpg.php`

## Network Traffic Analysis
Some useful Wireshark http filters.

- `http.request.method == “METHOD”`  
    Hunting for repeated or unusual requests can be useful
- `http.request.uri contains “.php”`  
    Can be helpful in finding suspicious or modified files
- `http.user_agent`   
    Used to locate unusual or outdated User-Agents