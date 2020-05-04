[title]: # (Server Onboarding)
[tags]: # (remote access controller)
[priority]: # (200)
# Best Practices - Server Onboarding

## Unix/Linux Servers

These guidelines are found to be helpful for system administrators who are attaching Unix and/or Linux servers:

* Identify useful information – In order to attach servers to Remote Access Controllers you will need to make a list of IP address or DNS of servers, which port is SSH running on, what MFA policy should be applied and more. Its best to decide on policies to protect servers, and logically group in them in clusters before the onboarding process starts.
* Provisioning accounts – Every customer is somewhat unique. You need to decide beforehand whether root accounts, with passwords can be used to onboard servers or not. If not whether SSH keys for the root account can be used. If not please identify sudo enabled accounts, and whether passwords or keys are going to be used prior to the onboarding.
* Identify ports and Authentication Mechanism – Since standard services like SSH may be running on non standard ports, please identify the correct port lists and what type of authentication is used – options range from password based, to keys, to LDAP/AD.
* Test network connectivity – Often time network connections that are assumed to be available are not. Please SSH into the Remote Access Controllers on premise instances or your AWS AMI instances and make sure that network connectivity to some sample servers, and your directory service is actually present before onboarding.
* Investigation data – It might be necessary to debug any issues that are non obvious or are not easily presented via error messages from the Remote Access Controllers dashboard. In this case please share the /var/log/syslog from the Remote Access Controllers virtual machines with the Remote Access Controllers team.

## Windows Servers

The above points apply to Windows servers too but with some changes. Please keep in mind that services like RDP and their associated ports need to be identified and appropriately used during the onboarding process. The points below are in
addition to the above:

* Domain servers – Since domain servers do not have local accounts, customer may use AD enabled remote accounts to attach these servers to Remote Access Controllers. Please make sure that the account used to attach a domain enabled server to Remote Access Controllers, is part of AD, and that this account is synced up with Remote Access Controllers in the users and groups area of the Remote Access Controllers dashboard.
* Non Domain servers – These servers are really simple to add to Remote Access Controllers, simply use the Administrative credentials and please refer to the points below for RDP ports and Server Preparation.
* RDP ports – Please verify and document which ports RDP is running on to use during the provisioning. Please remember to input 3389 the default RDP into the GUI when attaching a server.
* AD/LDAP authentication – Please verify that AD/LDAP is integrated with Remote Access Controllers prior to onboarding if you want to use AD/LDAP as your authentication mechanism.
* Server Preparation - Prior to adding a server to Remote Access Controllers you will need to run two helper powershell scripts on the Windows machine. These scripts can be removed afterwards. These scripts called WindowsPrep.ps1 and GuacADEnable.ps1 need to be run sequentially, as an Administrator on the Windows machine. These scripts will modify firewall rules to allow Remote Access Controllers to connect to these machines. Please contact your Remote Access Controllers representative for these two scripts.
* Domain Server Username - When adding a domain controlled Windows server please keep in mind that the DOMAIN field in the GUI for the add server modal needs the NETBIOS name like “RAC”. Further the username of the account being used to add the server must include the NETBIOS name as well. Example – “RAC\jdoe”.
