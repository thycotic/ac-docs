[title]: # (Users & Groups)
[tags]: # (thycotic access control)
[priority]: # (5)
# Users and Groups

## Users

![users](images/users.png "Users table")

The Users table shows the users that belong to your organization.

For each user you can view basic information such as username, first & last name, role, and group. The __Installation Step__ column shows which part of the installation process has been completed by the user. The __Installation Step__ indicator allows you to track user progress and decide if the user needs further assistance.

The __User Table__ is also used to manage and change user accounts.

## Create User

To create a user

1. At the top right hand corner of the main panel, click __Add User__.
2. From the popup window, enter the user’s information into the displayed fields.
3. Select the role and group that you want the user to be assigned.
4. Click __Create User__ for the changes to take effect.

>**Caution**: Assigning the __Admin__ role to a user will allow them to login and change settings in the Access Control panel. Additionally, any manual user additions or deletions could cause inconsistencies if your organization has an LDAP service running.

![ldap warning](images/ldap-warning.png "LDAP inconsistency warning for manual user maintenance")

### Share User Credentials

Share a user’s credentials by clicking the __share__ icon under user’s username.

![share](images/share-user.png "Share user icon") - ![share](images/share-user-2.png "Share modal")

For more info refer to [Share account credentials in the Applications](../applications/cfg.md#share_account_credentials) section.

### Handle User Access Requests

A user might not have the permissions to access certain URLs or Elements that are blocked by the group they belong to. Refer to [Set Privileged URLs & View/Remove Blocked Elements](../applications/cfg.md#set_privileged_urls). However, they can request access to some restricted elements through the browser extension.

These requests can be displayed by clicking __info__ under the user’s username. From the popup window that comes up, you can review the request and inform the user if his access was granted or rejected.

![access req](images/access-req.png "User access requests")

>**Important**: If you decide to grant access for an element (or URL) to a user, you have to do this manually by adding the user to a group that already has access to the specific element. For example, user A belongs to group G that restricts access to an element E. User A requests access to E. Organization admin can either create a new group that allows access to this element (See Create Organization Group for more info) or add user A to a group H that already have access to element E.

### Edit User

If you wish to edit a user’s data click the button under __Actions__ column. Form this page, you can edit a user’s personal information, assign him a new role and/or add him in a new group. Remember to click __Update user__ for changes to take effect.

Copy a user by clicking on the   button under __Actions__ column.

### Delete User

If you wish to delete a user click the  button under __Actions__ column. This action will perform a soft delete, which means that the user can be retrieved if needed in the future.

![soft delete](images/soft-del.png "Soft deleted user")

In case you want to delete a user permanently, click the __Hard delete__ button after soft delete has been performed. You may also recover the user.

![hard delete](images/hard-del.png "Recover or hard delete a user")

>**Important**: You have to be careful before deleting a user. There might be inconsistencies if an LDAP service is running.

### Provision to Accounts

If you wish to grant access for a user to one or more applications or servers, click on the __provision to accounts__ icon.

![provision](images/prov-to-accts-1.png "Provision to accounts icon") - ![provision](images/prov-to-accts.png "Provision to accounts modal")

This feature will allow users to login to either the selected applications by using newly generated credentials, or the selected servers by choosing one of the existing accounts.

#### Grant User Access to Servers

In the displayed popup window, click __Servers__ radio button and then choose the server you would like to give access to. Then choose one or more accounts that will be given to the user in order to be able to login to the selected server.
<!--
![TODO](images/prov-acct-servers.png "Provision to accounts - Servers") -->

Remember to click __Update__ for your changes to take effect.

<!-- #### Grant User Access to Application

In the displayed popup window, click __Applications__ radio button and then choose one or more applications in which you would like the user to be able to login.

![TODO](images/prov-acct-apps.png "Provision to accounts - Applications") 

The request will be handled by Onion ID Admins and your user will then have access to the selected apps. -->

## Send Initial Registration Code Reminder

It is quite common for users to forget their Initial Registration code. You can send them a reminder email with their code by clicking __Remind Rec Code__ under the __Actions__ column.

### Re-invite User

If you wish to resend the registration email to the user once again, click __Re-Invite__ under the __Actions__ column.

## Import Users to Organization

In order to import users into your organization, click __GA/Okta Import__ located on the top of the main panel. From the pop-up window that comes up, select between Google Apps or OKTA depending on the import type you want.

Via the __User & Groups__ | __Imports__ menu option, you can import users from __LDAP__ and via __CSV Import__.

### Import Users from Google Apps

Detailed step by step instructions are provided when __Google Apps__ option is selected from the __Select import type__ drop down menu.

### Import Users from OKTA

Detailed step by step instructions are provided when __ΟΚΤΑ__ option is selected from the __Select import type__ drop down menu.

### Delete All LDAP Users

Requirements: You must have imported users from LDAP to perform this action. See in __Import Users from LDAP__ for more info.

If you wish to delete every user that has been previously imported from LDAP, click the __Delete All LDAP Users__ button. We strongly advise you to use this option only when it’s really necessary and in cases of a faulty or mistaken LDAP import.

>**Caution**: Users are going to be deleted permanently!

### Import Users from CSV

Navigate to __User & Groups__ | __Imports__ and select the __CSV Import Job__ tab. Choose the csv file to import. 

![csv](images/csv.png "CSV import")

A CSV sample is available to help you understand the desired format of the uploaded CSV, click on the __Sample CSV__ button at the right of the file path field.

### Import User from LDAP/AD

Thycotic Access Control provides you with the capability to import users from your Active Directory/ies into your organization.

Before importing Users, make sure to open the **Required Ports** for LDAP/AD

|    Traffic    |    Port(s)    |    Direction    |
|---|---|---|
|LDAP | 389 - TCP | Inbound|
|LDAP(S)| 636 - TCP | Inbound |

<br>

To import from LDAP

1. Select LDAP from the __Select import type__ drop-down menu.
    ![ldap import](images/ldap.png "LDAP import")
1. Input the **LDAP Service Hostname** of the Active Directory or other LDAP server.
1. Input the **LDAP Service Port** that the server answers to.
1. Check the box **Active Directory** box if Access Controller is going to import users from an Active Directory.
1. Input the **Username** and **password** used to log in to the LDAP server.
1. If the server requires a certificate, copy and paste the **Certificate Content**.
1. Check the **Use SSL** or **Use SSLv3** box that corresponds to the server.
1. Input the **Searchbase** location in the LDAP directory that Access Controller LDAP will start looking for users and/or groups.
1. Check **Import Groups** to import user groups.
1. Choose the **Debug Level** from the drop-down menu.
    * __Info__ will provide basic log data from the LDAP service.
    * __Debug__ will provide advanced logging.
1. Input the **Update Time** that sets the interval between consecutive LDAP import requests. 
    > **NOTE**: Time is set in minutes, so please take caution before setting this field. For example, 1440 m (= 1 day) or 2880 m (= 2 days) would be accepted input.

#### Attribute Mappings/Advanced Import Settings/Import Filtering

* **Attribute Mappings**: A list of active directory attributes to be imported for every user in the Access Controller Panel. Input the corresponding **attribute name** used in the in **LDAP schema**.
* **Advanced Import Settings** Specify the default group, if server sync is wanted, and select to optimize LDAP queries.
* **Import Filtering**: Specify filter settings based on available drop-down options.

![ldap import 2](images/ldap-2.png "LDAP import mappings and settings")
