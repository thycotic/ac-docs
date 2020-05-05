[title]: # (Ports)
[tags]: # (thycotic access control)
[priority]: # (3)
# Ports and Connections

This VM consists of 4 different services: The OID panel, the  RDP proxy, the SSH proxy and the LDAP/AD sync agent. The panel communicates internally with the other three services either using their FQDN through HTTPS or through the loopback interface.

| **Linux VM** | |
| ----- | ----- |
| **Incoming connections** | |
| TCP 80 | Access to the OID dashboard and RDP proxy web client. Can be used interchangeably with 443 if HTTPS is enabled. |
| TCP 443 | Access to the OID dashboard and RDP proxy web client. |
| TCP 4443  | Used by the OID browser extension (installed on the users’ workstations) and mobile app to register to/access the OID panel. Also, used for calls to the OID API internally. It needs to be open to the internet, if workstations and mobile devices access OID from outside the organisation’s network. |
| TCP 2222  | From IPs that will use the SSH proxy. |
| TCP 22 | SSH connections from administrative IPs. Used by Administrators to access the VM. |
| **Outgoing connections** | |
| TCP 80 | Used internally by the instance. |
| TCP 443  | Used internally by the instance. |
| TCP 4443 | Used internally by the instance. |
| TCP 53 | For DNS queries |
| TCP 2222 | To the Windows VM to enable Windows server provisioning |
| TCP 3389 | RDP proxy connections to the target Windows servers |
| TCP 7443 | Connection to Onion ID router server (https://router.onionid.com) to handle browser extension and mobile app registrations. |
| | **NOTE 1**: router.onionid.com points to an ELB, so it may have multiple IP addresses. This needs DNS whitelisting. |
| | **Note 2**: The users’ workstations and mobile devices will also need to access router.onionid.com to that port, to register the OID browser extension and OID mobile app respectively. |
| TCP 22 | SSH connections from the SSH proxy to target hosts managed by Onion ID. |

| **Windows VM** | |
| ----- | ----- |
| **Incoming connections** | |
| TCP 2222 | SSH connections from the Linux VM to manage Windows server provisioning. |
| TCP 3389 | RDP connections from administrative IPs. Used by Administrators to access the VM. |
| **Outgoing connections** | |
| TCP/UDP 135 | Connections to the Windows Management Instrumentation (WMI) service for target Windows machines. |
| TCP 137 | NetBIOS name/datagram services - Connections to target Windows machines |
| TCP 138 | NetBIOS name/datagram services - Connections to target Windows machines |
| TCP 139 | NetBIOS - Connections to target Windows machines |
| TCP/UDP 445 | SMB - Connections to target Windows machines |
