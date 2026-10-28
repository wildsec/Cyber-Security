**NetBIOS** or **Net**work **B**asic **I**nput/**O**utput **S**ystem is the technology responsible for allowing applications on different hosts to communicate with each other.

| **Notes**                                                                                                                                                                          | **Wireshark Filter**             |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| Global search.                                                                                                                                                                     | - `nbns`                         |
| **"NBNS"** options for grabbing the low-hanging fruits:<br><br>- **Queries:**Query details.<br>- Query details could contain **"name, Time to live (TTL) and IP address details"** | - `nbns.name contains "keyword"` |
