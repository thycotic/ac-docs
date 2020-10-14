[title]: # (Network Requirements)
[tags]: # (thycotic access control)
[priority]: # (2)

# Network Requirements

The chart below shows standard ports for specific functions in Remote Access Controller, Cloud Access Controller, and Database Access Controller. **These ports need to be available inbound to the corporate network from wherever Access Controller is deployed.** Non-standard ports for specific functions such as RDP and SSH can be configured in Remote Access Controller. 

If you are using the Thycotic-hosted Access Controller deployment, **Thycotic suggests limiting inbound traffic to the protocols below  using the Access Controller Suite IP address space applicable to your region.** Please reach out to your Thycotic account representative to obtain the relevant IP addresses for your region.

## Required Ports

|    Item    |    Traffic    |    Port(s)    |    Direction    |
|---|---|---|---|
| Directory Synchronization | LDAP | 389 - TCP | Inbound|
||LDAP(S)| 636 - TCP | Inbound |
|Linux (Remote Access Controller) | SSH | 22 - TCP | Inbound
| Windows (Remote Access Controller) |SMB|TCP 445|Inbound|
||RDP| TCP 3389|Inbound|
||WinRM| 5985 - TCP|Inbound|
||ALL ICMP - PIv4 Ports| N/A|Inbound|
|Web Applications (Cloud Access Controller)|TCP|Varies by Web Application (Commonly 443, 8443, etc)|Inbound|
|Databases (Database Access Controller)|TCP|Varies by Database|Inbound|
|Access Controller Browser Extension|TCP|4443 - TCP|Outbound|

## Account Permission Requirements
|Thycotic Access Controller Functions|Permissions|
|---|---|
|Window|Local Administrator|
|Linux|Sudo Privileges|
|Database|Any|
|Web Application|Any|
