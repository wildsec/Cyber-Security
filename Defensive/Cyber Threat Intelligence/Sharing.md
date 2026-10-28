**Traffic Light Protocol (TLP)** is a four-tier classification system that dictates how threat intelligence can be shared:

- **CLEAR**: No restrictions—share anywhere  
- **GREEN**: Share with peers/community only, not publicly  
- **AMBER**: Internal use only; external sharing requires need-to-know basis  
- **RED**: Named recipients only, highly restricted  

SOC analysts must preserve TLP labels when moving IOCs between platforms. Mishandling violates contracts and damages partner trust.

## Sharing and Processing Intel

- **STIX**: a JSON schema for machine-readable threat data.
- **TAXII**: The Trusted Automated eXchange of Indicator Information is a set of secure APIs used to exchange threat intelligence in near real-time for detection, prevention, and mitigation of threats.  
    It supports two sharing models: **Collection**, which ensures threat intel is collected and hosted by a producer, and **Channel**, which publishes threat intel to users from a central server.

