[title]: # (Network Requirements)
[tags]: # (thycotic access control)
[priority]: # (3)

# Network Requirements

The chart below shows standard ports for specific functions in Remote Access Controller, Cloud Access Controller, and Database Access Controller. **These ports need to be available inbound to the corporate network from wherever Access Controller is deployed.** Non-standard ports for specific functions such as RDP and SSH can be configured in Remote Access Controller. 

If you are using the Thycotic-hosted Access Controller deployment, **Thycotic suggests limiting inbound traffic to the protocols below  using the Access Controller Suite IP address space applicable to your region.** Please reach out to your Thycotic account representative to obtain the relevant IP addresses for your region.

## Required Ports

> **Note:** Thycotic has created a set of PowerShell scripts that can be run on any Windows server and will open the necessary ports listed below. Please see the [Windows Server Preparation](../admin/servers/index.md) section to obtain the scripts and to learn more about adding Windows servers to Remote Access Controller.

|    Item    |    Traffic    |    Port(s)    |    Direction    |
|---|---|---|---|
| Directory Synchronization | LDAP | 389 - TCP | Inbound|
||LDAP(S)| 636 - TCP | 
|Linux (Remote Access Controller) | SSH | 22 - TCP | Inbound
| Windows (Remote Access Controller) | WMI | 22 - TCP | Inbound |
||SMB| 445 - TCP/UDP||
||RDP| 3389 - TCP/UDP||
||WinRM| 5985 - TCP||
||ALL ICMP - PIv4 Ports| N/A||
|Web Applications (Cloud Access Controller)|TCP|Varies by Web Application (Commonly 443, 8443, etc)|Inbound|
|Databases (Database Access Controller)|TCP|Varies by Database|Inbound|
|Access Controller Browser Extension|TCP|4443 - TCP|Outbound|

## Account Permission Requirement
|Item|Permissions|
|---|---|
|Window|Local Administrator|
|Linux|Sudo Privileges|
|Database|Any|
|Web Application|Any|

## Windows Server Preparation

To make onboarding of Windows server to Remote Access Controller simple, Thycotic provides these PowerShell scripts to run on the local machine targeted for onboarding.

### Windows Server (Non-domain Joined)

> **IMPORTANT:** Make sure you use an account with execution privileges and that the local accounts you are providing access through Access Controller are members of the Remote Desktop Users group.

1. Download the zip file containing the prep scripts and extract its contents.
1. Store the “WindowsPrep.ps1” script on the target Windows server.
1. On the target server, click Start, type “PowerShell”, and then click on “Windows PowerShell”.
1. In the PowerShell window navigate to the location where the script was stored.
1. Type “WindowsPrep.ps1” and press Enter.

### Windows Server (Domain Joined)

Before provisioning, two PowerShell scripts need to be run on the target server, which configure it accordingly. To run the scripts, follow the instructions below.

> **IMPORTANT:** Make sure you use an account with execution privileges and that the local accounts you are providing access through Access Controller are members of the Remote Desktop Users group.

1. Download the zip file containing the prep scripts and extract its contents
1. Store the “WindowsPrep.ps1”and “GuacADEnable.ps1” scripts on the target Windows server.
1. On the target server, click Start, type “PowerShell”, and then click on “Windows PowerShell”.
1. In the PowerShell window, navigate to the location where the scripts were stored.
1. Type “WindowsPrep.ps1” and press Enter.