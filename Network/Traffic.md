We can group the sources into two categories:

- Intermediary
- Endpoint

The flows we can also group into two categories:

- North-South: Traffic that exits or enters the LAN and passes the firewall
- East-West: Traffic that stays within the LAN (including LAN that extends to the cloud)

**Intermediary Sources**  
These are devices through which traffic mostly passes. While they generate some traffic, it is significantly lower than what endpoint devices generate. Under this category, we can find firewalls, switches, web proxies, IDS, IPS, routers, access points, wireless LAN controllers, and many more. Maybe less relevant for us, but all the infrastructure of Internet Service Providers is also considered part of this category.

The traffic that originates from these devices comes from services like routing protocols (EIGRP, OSPF, BGP), management protocols (SNMP, PING), logging protocols (SYSLOG), and other supporting protocols (ARP, STP, DHCP).

**Endpoint Sources**  
These are devices where traffic originates and ends. Endpoint devices take the bulk of the network bandwidth. Devices that fall under this category are servers, hosts, IoT devices, printers, virtual machines, cloud resources, mobile phones, tablets, and many more.

**North-South Traffic**  
NS traffic is often monitored closely as it flows from the LAN to the WAN and vice versa. The most well-known services in this category are client-server protocols like HTTPS, DNS, SSH, VPN, SMTP, RDP, and many more. Each of these protocols has two streams: ingress (inbound) and egress (outbound). All of this traffic passes the firewall in one way or another. Configuring firewall rules and logging properly are key to visibility.

**East-West Traffic**  
EW traffic stays within the corporate LAN, so it is often monitored less. However, it is important to keep track of these flows. When the network is compromised, an attacker will often exploit different services internally to move laterally within the network. 

Directory, Authentication & Identity Services
- Kerberos / LDAP: Authentication/queries to Active Directory
- RADIUS / TACACS+: Network access control
- Certificate Authority issuing internal certifications
File shares & print services
- SMB/CIFS: Accessing network drives
- IPP/LPD: Printing over the network
Router, switching, and infrastructure services
- DHCP traffic between hosts and the DHCP server
- ARP broadcast messages
- Internal DNS
- Routing protocol messages
Application Communication
- Database Connections: SQL over TCP
- Microservices APIs: REST or gRPC calls between services
Backup & Replication
- File Replication: Between data centers or to backup servers
- Database Replication: MySQL binlog replication, PostgreSQL streaming, and more
Monitoring & Management
- SNMP: Device health metrics
- Syslog: Centralized logging
- NetFlow/IPFIX: Traffic flow telemetry
- Other endpoint logs sent to a central logging server

