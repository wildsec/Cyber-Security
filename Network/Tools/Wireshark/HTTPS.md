[[HTTP(S)]]
You can use the "right-click" menu or **"Edit --> Preferences --> Protocols --> TLS"** menu to add/remove key log files.

| **Notes**                                                                                                                                                                                                                                                                                                                                              | **Wireshark Filter**                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| **"HTTPS Parameters"** for grabbing the low-hanging fruits:<br><br>- **Request:** Listing all requests<br>- **TLS:** Global TLS search<br>- TLS Client Request<br>- TLS Server response<br>- Local Simple Service Discovery Protocol (SSDP)<br><br>**Note:** SSDP is a network protocol that provides advertisement and discovery of network services. | - `http.request`<br><br>- `tls`<br><br>- `tls.handshake.type == 1`<br><br>- `tls.handshake.type == 2`<br><br>- `ssdp` |
![[Pasted image 20260309133230.png]]

- Client Hello: `(http.request or tls.handshake.type == 1) and !(ssdp)` 
- Server Hello: `(http.request or tls.handshake.type == 2) and !(ssdp)`
![[Pasted image 20260309133255.png]]![[Pasted image 20260309133301.png]]