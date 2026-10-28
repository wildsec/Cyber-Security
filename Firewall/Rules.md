## Rules
The basic components of a firewall’s rule are described below:

- **Source address:** The machine’s IP address that would originate the traffic.
- **Destination address:** The machine’s IP address that would receive the data.
- **Port:** The port number for the traffic.
- **Protocol:** The protocol that would be used during the communication.
- **Action:** This defines the action that would be taken upon identifying any traffic of this particular nature.
- **Direction:** This field defines the rule’s applicability to incoming or outgoing traffic.

### Types of Action
* Allow -> traffic would be permitted
* Deny -> traffic would be blocked and not permitted
* Forward -> redirects traffic to a different network segment using the forwarding rules created on the firewalls

### Directionality
##### Inbound Rules
Rules are categorized as inbound rules when they are meant to be applied to incoming traffic only.
##### Outbound Rules
These rules are made for outgoing traffic only. 
##### Forward Rules
Forwarding rules are created to forward specific traffic inside the network. 