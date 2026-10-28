
## Telnet
TELNET (Teletype Network) protocol is a network protocol for remote terminal connection.
connect to any server listening on a TCP port number.

```
telnet MACHINE_IP PORT

Trying 10.49.191.214... 
Connected to 10.49.191.214. 
Escape character is '^]'. 

GET / HTTP/1.1

```

## DHCP 
DHCP relies on UDP and server listens on Port 67 and client send from Port 68.

DORA
1. **DHCP Discover**: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
2. **DHCP Offer**: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
3. **DHCP Request**: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
4. **DHCP Acknowledge**: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

## ARP
Address Resolution Protocol (ARP) makes it possible to find the MAC address of another device on the Ethernet. On same network communication is with MAC addresses.
An ARP Request or ARP Reply is not encapsulated within a UDP or even IP packet; it is encapsulated directly within an Ethernet frame.
If we use `tcpdump`, the packets will be displayed differently. It uses the terms ARP **Request** and ARP **Reply**. For your information, the output is shown in the terminal below.


## FTP
FTP server listens on TCP port 21 by default;

Example commands defined by the FTP protocol are:

- `USER` is used to input the username
- `PASS` is used to enter the password
- `RETR` (retrieve) is used to download a file from the FTP server to the client.
- `STOR` (store) is used to upload a file from the client to the FTP server.