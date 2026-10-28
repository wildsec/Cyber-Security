``` bash
# OS and Filesystem Discovery
pwd
ls /
env
uname -a
lsb_release -a
hostname

# User and Groups Discovery
id
whoami
w
last
cat /etc/sudoers
cat /etc/passwd

# Process and Network Discovery
ps aux
top
ip a
ip r
arp -a
ss -tnlp
netstat -tnlp

# Cloud or Sandbox Discovery
systemd-detect-virt
lsmod
uptime
pgrep "<edr-or-sandbox>"

# Specialized Discovery — Credential / Sensitive Data Hunting
history | grep pass
find / -name .env
find /home -name id_rsa

# Specialized Discovery — Crypto Mining Suitability Checks
cat /proc/cpuinfo
lscpu | grep Model
free -m
top
htop

# Specialized Discovery — Internal Network Reconnaissance
ping <ip>
for ip in 192.168.1.{1..254}; do nc -w 1 $ip 22; done
```

## Detection
![[Pasted image 20260315095821.png]]