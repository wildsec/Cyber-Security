|                     |                                                                                                                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Capture Filters** | This type of filter is used to save only a specific part of the traffic. It is set before capturing traffic and not changeable during the capture. |
| **Display Filters** | This type of filter is used to investigate packets by reducing the number of visible packets, and it is changeable during the capture.             |

**Note:** You cannot use the display filter expressions for capturing traffic and vice versa.

### Capture Filter Syntax
- **Scope:** host, net, port and portrange.
- **Direction:** src, dst, src or dst, src and dst,
- **Protocol:** ether, wlan, ip, ip6, arp, rarp, tcp and udp.
- **Sample filter to capture port 80 traffic:** `tcp port 80`
Docu: https://www.wireshark.org/docs/man-pages/pcap-filter.html

### Display Filter Syntax
**Sample filter to capture port 80 traffic:** `tcp.port == 80`
A quick reference is available under the **"Analyse --> Display Filters"** menu.

| **English** | **C-Like** | **Description**          | **Example**                                                                                                                                                                                      |
| ----------- | ---------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| eq          | ==         | Equal                    | `ip.src == 10.10.10.100`                                                                                                                                                                         |
| ne          | !=         | Not equal                | `ip.src != 10.10.10.100`                                                                                                                                                                         |
| gt          | >          | Greater than             | `ip.ttl > 250`                                                                                                                                                                                   |
| lt          | <          | Less Than                | `ip.ttl < 10`                                                                                                                                                                                    |
| ge          | >=         | Greater than or equal to | `ip.ttl >= 0xFA`                                                                                                                                                                                 |
| le          | <=         | Less than or equal to    | `ip.ttl <= 0xA`                                                                                                                                                                                  |
| and         | &&         | Logical AND              | `(ip.src == 10.10.10.100) AND (ip.src == 10.10.10.111)`                                                                                                                                          |
| or          | \|         | Logical OR               | `(ip.src == 10.10.10.100) OR (ip.src == 10.10.10.111)`                                                                                                                                           |
| not         | !          | Logical NOT              | `!(ip.src == 10.10.10.222)`<br><br>**Note:** Usage of `!=value` is deprecated; using it could provide inconsistent results. Using the `!(value)` style is suggested for more consistent results. |
### IP Filters
IP filters help analysts filter the traffic according to the IP level information from the packets (Network layer of the OSI model [[Layers OSI]])

| Filter                       | Description                                                                                                                                                 |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ip`                         | Show all IP packets.                                                                                                                                        |
| `ip.addr == 10.10.10.111`    | Show all packets containing IP address 10.10.10.111.                                                                                                        |
| `ip.addr == 10.10.10.0/24`   | Show all packets containing IP addresses from 10.10.10.0/24 subnet.                                                                                         |
| `ip.src == 10.10.10.111`     | Show all packets originated from 10.10.10.111                                                                                                               |
| `ip.dst == 10.10.10.111`     | Show all packets sent to 10.10.10.111                                                                                                                       |
| ip.addr **vs** ip.src/ip.dst | **Note:** The ip.addr filters the traffic without considering the packet direction. The ip.src/ip.dst filters the packet depending on the packet direction. |
### TCP and UDP Filters
TCP filters help analysts filter the traffic according to protocol-level information from the packets (Transport layer of the OSI model [[Layers OSI]]).

| Filter                | Description                                     | Filter                | Expression                                      |
| --------------------- | ----------------------------------------------- | --------------------- | ----------------------------------------------- |
| `tcp.port == 80`      | Show all TCP packets with port 80               | `udp.port == 53`      | Show all UDP packets with port 53               |
| `tcp.srcport == 1234` | Show all TCP packets originating from port 1234 | `udp.srcport == 1234` | Show all UDP packets originating from port 1234 |
| `tcp.dstport == 80`   | Show all TCP packets sent to port 80            | `udp.dstport == 5353` | Show all UDP packets sent to port 5353          |

| **Notes**                                                                                | **Filters**                                                                    |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Global search.                                                                           | - `tcp`<br><br>- `udp`                                                         |
| - Only SYN flag.<br>- SYN flag is set. The rest of the bits are not important.           | - `tcp.flags == 2`<br><br>- `tcp.flags.syn == 1`                               |
| - Only ACK flag.<br>- ACK flag is set. The rest of the bits are not important.           | - `tcp.flags == 16`<br><br>- `tcp.flags.ack == 1`                              |
| - Only SYN, ACK flags.<br>- SYN and ACK are set. The rest of the bits are not important. | - `tcp.flags == 18`<br><br>- `(tcp.flags.syn == 1) and (tcp.flags.ack == 1)`   |
| - Only RST flag.<br>- RST flag is set. The rest of the bits are not important.           | - `tcp.flags == 4`<br><br>- `tcp.flags.reset == 1`                             |
| - Only RST, ACK flags.<br>- RST and ACK are set. The rest of the bits are not important. | - `tcp.flags == 20`<br><br>- `(tcp.flags.reset == 1) and (tcp.flags.ack == 1)` |
| - Only FIN flag<br>- FIN flag is set. The rest of the bits are not important.            | - `tcp.flags == 1`<br><br>- `tcp.flags.fin == 1`                               |
### Application Level Protocol Filters | HTTP and DNS
Application-level protocol filters help analysts filter the traffic according to application protocol level information from the packets (Application layer of the OSI model [[Layers OSI]]).

| Filter                          | Description                                    |
| ------------------------------- | ---------------------------------------------- |
| `http`                          | Show all HTTP packets                          |
| `http.response.code == 200`     | Show all packets with HTTP response code "200" |
| `http.request.method == "GET"`  | Show all HTTP GET requests                     |
| `http.request.method == "POST"` | Show all HTTP POST requests                    |

| Filter                    | Description              |
| ------------------------- | ------------------------ |
| `dns`                     | Show all DNS packets     |
| `dns.flags.response == 0` | Show all DNS requests    |
| `dns.flags.response == 1` | Show all DNS responses   |
| `dns.qry.type == 1`       | Show all DNS "A" records |
## Display Filter Expressions
Easy-to-use display filter builder guide. It is available under the **"Analyse --> Display Filter Expression"** menu.

## Advanced Filtering
| Filter      |
| ----------- |
| `contains`  |
| ``matches`` |
| ``in``      |
| upper()     |
| lower()     |
| `string()`  |
