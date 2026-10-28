Windows: `winpcap`

``` bash
-i INTERFACE
-i any
-i eth0

#Show available network interfaces
ip a s

#Filtering
host HOSTNAME
src host IP
src host HOSTNAME
dst host IP
dst host HOSTNAME

port 53
src port PORT_NUMBER
dst port PORT_NUMBER

tcpdump PROTOCOL

#Logical
and, or, not


```

| Command                | Explanation                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| `tcpdump -i INTERFACE` | Captures packets on a specific network interface                  |
| `tcpdump -w FILE`      | Writes captured packets to a file                                 |
| `tcpdump -r FILE`      | Reads captured packets from a file                                |
| `tcpdump -c COUNT`     | Captures a specific number of packets                             |
| `tcpdump -n`           | Don’t resolve IP addresses                                        |
| `tcpdump -nn`          | Don’t resolve IP addresses and don’t resolve protocol numbers     |
| `tcpdump -v`           | Verbose display; verbosity can be increased with `-vv` and `-vvv` |

You can use `tcp[tcpflags]` to refer to the TCP flags field. The following TCP flags are available to compare with:

- `tcp-syn` TCP SYN (Synchronize)
- `tcp-ack` TCP ACK (Acknowledge)
- `tcp-fin` TCP FIN (Finish)
- `tcp-rst` TCP RST (Reset)
- `tcp-push` TCP Push

- `tcpdump "tcp[tcpflags] == tcp-syn"` to capture TCP packets with **only** the SYN (Synchronize) flag set, while all the other flags are unset.
- `tcpdump "tcp[tcpflags] & tcp-syn != 0"` to capture TCP packets with **at least** the SYN (Synchronize) flag set.
- `tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"`

|Command|Explanation|
|---|---|
|`tcpdump -q`|Quick and quite: brief packet information|
|`tcpdump -e`|Include MAC addresses|
|`tcpdump -A`|Print packets as ASCII encoding|
|`tcpdump -xx`|Display packets in hexadecimal format|
|`tcpdump -X`|Show packets in both hexadecimal and ASCII formats|
