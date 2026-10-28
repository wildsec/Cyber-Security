`~/.bash_history`

By default, commands are first stored in memory during your session, and then written to the per-user `~/.bash_history` file when you log out.


``` bash
history

# Problems:
## Attackers can simply add a leading space to the command to avoid being logged
ubuntu@thm-vm:~$  echo "You will never see me in logs!"

## Attackers can paste their commands in a script to hide them from Bash history
ubuntu@thm-vm:~$ nano legit.sh && ./legit.sh
 
## Attackers can use other shells like /bin/sh that don't save the history like Bash
ubuntu@thm-vm:~$ sh
$ echo "I am no longer tracked by Bash!"

```

