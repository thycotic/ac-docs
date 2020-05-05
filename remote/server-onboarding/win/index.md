[title]: # (Windows Server)
[tags]: # (thycotic access control)
[priority]: # (2)
# Windows Server Setup

The purpose of this topic is to provide instructions on how to prepare a Windows server to be provisioned with Thycotic Access Control. It also includes a troubleshooting guide to verify that a target server has been configured properly and that the necessary services are accessible. This is relevant mostly for on-prem installations of Thycotic Access Controllers. For issues with Windows server provisioning on the SaaS version please contact Thycotic Support.

## Windows Server Preparation (for Servers Not in a Domain)

For the access controller to be able to retrieve local accounts from a target Windows server, a number of services need to be accessible on that server. Before provisioning, a Powershell script needs to be run on that server, which configures it accordingly. To run the script, follow the instructions below.

>**Note**: Make sure you use a user with execution privileges.

1. Download the zip file containing the prep scripts and extract its contents.
1. Store the “WindowsPrep.ps1” script on the target Windows server.
1. On the target server, click Start, type “PowerShell”, and then click on “Windows PowerShell”.
1. In the PowerShell window, navigate to the location where the script was stored. 1. Type “WindowsPrep.ps1” and press Enter.

If the script returns an error, please contact support for assistance.

Make sure the local accounts you wish to provide access to through the access controller, are members of the Remote Desktop Users group.

You may now add the server to the Thycotic Access Controller.

## Windows Server Preparation (for Servers in a Domain)

Before provisioning, two Powershell scripts need to be run on the target server, which configure it accordingly. To run the scripts, follow the instructions below. Make sure you use a user with execution privileges.

1. Download the zip file containing the prep scripts and extract its contents.
1. Store the “WindowsPrep.ps1” and “GuacADEnable.ps1” scripts on the target Windows server.
1. On the target server, click Start, type “PowerShell”, and then click on “Windows PowerShell”.
1. In the PowerShell window, navigate to the location where the scripts were stored. 1. Type “WindowsPrep.ps1” and press Enter. 
1. Then, type “GuacADEnable.ps1” and press Enter.

If any of the scripts returns an error, please contact support for assistance.
You may now add the server to the Thycotic Access Controller.

## Troubleshooting (for On-prem Deployments)

If after preparing a Windows server, adding it to the Thycotic Access Controller does not work, you will need to ensure that the components involved in the provisioning process can connect to each other and the necessary services are
accessible.

### Confirm Connectivity between the Windows Proxy and the Target Server

On the Windows Proxy server, open a PowerShell terminal and execute the following command:

`net use \\<HOSTNAME>\ipc$ /u:<DOMAIN>\<USERNAME> "<PASSWORD>" /PERSISTENT:YES`

Where:

`HOSTNAME`: The hostname or IP address of the target server.
`DOMAIN`: The name of the domain the server belongs to (if applicable) or LOCALHOST.
`USERNAME`: The username of the user with administrative rights, used to provision the server.
`PASSWORD`: The password for the above user.

If the command returns an error, please check if the details entered in the command are correct, network
connectivity and firewall settings on the target server. For further assistance, please contact
support.

### Get Remote Local Accounts

On the Windows Proxy server, open a PowerShell terminal, navigate to the Desktop/provisioning folder and
execute the following command:
`.\GetRDaccounts.ps1 "<HOSTNAME>" "C:\Users\Administrator\Desktop\provisioning\output\testing_output" '<DOMAIN>\<USERNAME>' '<PASSWORD>'`

Where:

`HOSTNAME`: The hostname or IP address of the target server.
`DOMAIN`: The name of the domain the server belongs to (if applicable) or LOCALHOST.
`USERNAME`: The username of the user with administrative rights, used to provision the server.
`PASSWORD`: The password for the above user.

If the command was executed successfully you should see in the testing_output file the usernames of the local users
on the target server who are members of the Remote Desktop Users group.

For any other output, please check that there are users in the Remote Desktop Users group. Also check network
connectivity, firewall settings on the target server and if the details entered in the command are correct. For
further assistance, please contact support.

### PS Status Check

On the target server, open a PowerShell terminal, navigate to the Desktop/provisioning folder and execute the
following commands:

* `set-item wsman:\localhost\Client\TrustedHosts -value * -Force`
* `$pw = convertto-securestring -AsPlainText -Force -String '<PASSWORD>'`
* `$cred = new-object -typename System.Management.Automation.PSCredential -argumentlist '<DOMAIN>\<USERNAME>',$pw`
* `$session = new-pssession -ComputerName <HOSTNAME> -credential $cred`
* `Remove-PSSession -Id $session.Id`
* `net use /d \\<HOSTNAME>\\ipc$`

Where:

`HOSTNAME`: The hostname or IP address of the target server.
`DOMAIN`: The name of the domain the server belongs to (if applicable) or LOCALHOST.
`USERNAME`: The username of the user with administrative rights, used to provision the server.
`PASSWORD`: The password for the above user.

If the commands returns an error, please check if the details entered in the command are correct, network
connectivity and firewall settings on the target server. For further assistance, please contact
support.
