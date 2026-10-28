using [[System Calls]]

Instructions located in `/etc/audit/rules.d/` that define which system calls to monitor and which filters to apply:
![[Pasted image 20260315091112.png]]

You can view the generated logs in real time in `/var/log/audit/audit.log`, but it is easier to use the `ausearch` command, as it formats the output for better readability and supports filtering options.

## Alternatives
- [Sysmon for Linux](https://github.com/microsoft/SysmonForLinux): A perfect choice if you already work with Sysmon and love XML
- [Falco](https://falco.org/): A modern, open-source solution, ideal for monitoring containerized systems
- [Osquery](https://osquery.io/): An interesting tool that can be broadly used for various security purposes
- [EDRs](https://tryhackme.com/room/introductiontoedrs): Most EDR solutions can track and monitor various Linux runtime events

``` bash
# Show all audit events
ausearch

# Show recent events
ausearch -ts recent

# Show events since today
ausearch -ts today

# Show events in a specific time window
ausearch -ts 09:00:00 -te 11:00:00

# Search by event ID
ausearch -a <event_id>

# Search by hostname
ausearch -hn <hostname>

# Search by user ID (UID)
ausearch -ui <uid>

# Search by login user ID (AUID)
ausearch -ua <auid>

# Search by username
ausearch -ui 1000 | less

# Search by process ID
ausearch -p <pid>

# Search by executable path
ausearch -x /usr/bin/sudo

# Search by command name
ausearch -x bash
ausearch -x ssh
ausearch -x sudo
ausearch -x passwd

# Search for syscall activity
ausearch -sc execve
ausearch -sc open
ausearch -sc connect

# Search by file path
ausearch -f /etc/passwd
ausearch -f /etc/shadow
ausearch -f /etc/sudoers

# Search by key (if audit rules use keys)
ausearch -k identity
ausearch -k auth
ausearch -k privileged
ausearch -k access

# Search for login events
ausearch -m LOGIN

# Search for authentication events
ausearch -m USER_AUTH
ausearch -m USER_LOGIN
ausearch -m CRED_ACQ
ausearch -m CRED_DISP

# Search for account or user changes
ausearch -m ADD_USER
ausearch -m DEL_USER
ausearch -m CHUSER_ID
ausearch -m GRP_MGMT
ausearch -m ADD_GROUP
ausearch -m DEL_GROUP

# Search for privilege escalation / sudo-style activity
ausearch -x sudo
ausearch -m USER_CMD
ausearch -m USER_ACCT
ausearch -m CRED_REFR

# Search for command execution events
ausearch -sc execve
ausearch -m EXECVE

# Search for file permission or attribute changes
ausearch -m PATH
ausearch -f /etc/passwd
ausearch -f /etc/shadow

# Search for failed access / AVC denials (SELinux)
ausearch -m AVC
ausearch -m USER_AVC

# Search for network-related syscalls
ausearch -sc connect
ausearch -sc accept
ausearch -sc bind

# Search for daemon lifecycle events
ausearch -m DAEMON_START
ausearch -m DAEMON_END
ausearch -m DAEMON_ABORT
ausearch -m CONFIG_CHANGE

# Search for audit log tampering or config changes
ausearch -m CONFIG_CHANGE
ausearch -f /etc/audit/audit.rules
ausearch -f /etc/audit/rules.d/

# Search for kernel module activity
ausearch -sc init_module
ausearch -sc delete_module

# Search for time changes
ausearch -m TIME_CHANGE

# Search for suspicious use of sensitive binaries
ausearch -x usermod
ausearch -x passwd
ausearch -x chsh
ausearch -x sshd
ausearch -x su

# Interpret numeric values in human-readable form
ausearch -i

# Combine filters: recent sudo activity, interpreted
ausearch -ts recent -x sudo -i

# Combine filters: execve by a specific user since today
ausearch -ts today -ua <auid> -sc execve -i

# Combine filters: access to a sensitive file
ausearch -ts recent -f /etc/shadow -i

```

## Common SOC commands
```bash
# Commands executed recently
ausearch -ts recent -m EXECVE -i

# Sudo usage
ausearch -ts recent -x sudo -i

# Access to passwd/shadow/sudoers
ausearch -ts recent -f /etc/passwd -i
ausearch -ts recent -f /etc/shadow -i
ausearch -ts recent -f /etc/sudoers -i

# Authentication events
ausearch -ts recent -m USER_AUTH,USER_LOGIN,CRED_ACQ,CRED_DISP -i

# Account management changes
ausearch -ts recent -m ADD_USER,DEL_USER,ADD_GROUP,DEL_GROUP,CHUSER_ID,GRP_MGMT -i

# Network connection syscalls
ausearch -ts recent -sc connect -i

# Audit configuration changes
ausearch -ts recent -m CONFIG_CHANGE -i

# SELinux denials
ausearch -ts recent -m AVC,USER_AVC -i

```

## Nice Analyst Workflow
``` bash
# 1) Start with recent events
ausearch -ts recent -i

# 2) Look for command execution
ausearch -ts recent -m EXECVE -i

# 3) Check auth and login activity
ausearch -ts recent -m USER_AUTH,USER_LOGIN,CRED_ACQ,CRED_DISP -i

# 4) Check privileged command usage
ausearch -ts recent -x sudo -i
ausearch -ts recent -x su -i

# 5) Check sensitive file access
ausearch -ts recent -f /etc/shadow -i
ausearch -ts recent -f /etc/sudoers -i

# 6) Check network-related syscalls
ausearch -ts recent -sc connect -i

# 7) Check for audit rule tampering
ausearch -ts recent -m CONFIG_CHANGE -i
```