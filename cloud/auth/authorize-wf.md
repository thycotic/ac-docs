[title]: # (Authorization Workflow)
[tags]: # (cloud access controller)
[priority]: # (202)
# Authorization Workflow

Cloud Access Controller can implement various types of command introspection, user provisioning, multi factor authentication, script execution control and more on each server that is registered with the Cloud Access Controller system.

# Auditing workflow

Cloud Access Controller helps with auditing user actions on any piece of infrastructure. From
history of commands, to video session recordings that are searchable by keywords, is available. Additionally, customers will use the reporting section to generate compliance reports that can be shared with the audit team to reduce the amount of time needed for compliance processes.

## Integration with Scripts

Cloud Access Controller is easy to integrate with bash/python scripts. A common finding is that
scripts contain either (1) hard coded credentials or (2) SSH keys to login to servers and perform various tasks. Cloud Access Controller works as a gateway solution and since it has changed credentials for user accounts associated with servers, can force employees and scripts to visit the infrastructure through Cloud Access Controller.

Typical examples of using scripts with Cloud Access Controller would be bash scripts that run as a service to pull statistics from various servers. There is only one change that needs to be made to existing scripts: Changing the connection string from something like

`ssh –p 2222 scriptuser\@server.com`
to
`ssh –p 2222 scriptuser\~server.com\@ssh.onionid.com`

The above forces the connection to pass through the Cloud Access Controller system and allows
Cloud Access Controller to make sure the script cannot be misused. Furthermore, Cloud Access Controller tracks exactly how the script is accessing a server. Usage of SSH keys within the
script is acceptable and recommended. There is no need to change the SSH keys used by the script. It is recommended that all script based access be tied to a policy on the Cloud Access Controller system to prevent any misuse. The policy may have “autologin“ enabled with whitelisted IP ranges to make sure scripts being run only within the data center can access the servers.

Moreover, Cloud Access Controller makes it really easy for scripts to be “owned“ by different
AD accounts and be able to access a different privileged account on the server without knowing the credentials for the privileged account. As an example, the command below can help a script login to a server as a privileged account without knowing the actual SSH key for the privileged account.

```
ssh –p 2222
scriptuser\~service-account-on-the-server\~server.com\@ssh.onionid.com
```
