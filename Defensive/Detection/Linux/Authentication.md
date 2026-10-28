`/var/log/auth.log` (or `/var/log/secure` on RHEL-based systems)

Contains:
- Authentication events
- user managment events
- launched sudo commands
- more..

![[Pasted image 20260315085757.png]]

``` bash
# Login and Logout Events
cat /var/log/auth.log | grep -E 'session opened|session closed'
# SSH daemon login
cat /var/log/auth.log | grep "sshd" | grep -E 'Accepted|Failed'
# password change, user deletion, and then privileged user creation
cat /var/log/auth.log | grep -E '(passwd|useradd|usermod|userdel)\['
# sudo commands
cat /var/log/auth.log | grep -E 'COMMAND='

```