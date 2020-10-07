[title]: # (Groups)
[tags]: # (thycotic access control)
[priority]: # (6)
# Create Group

Use Groups to assign identical permissions to multiple users. Users in a Group share applications and privileges. 

To create a Group
1. Click **Add Group** in the top right-hand corner of the main panel.

![new Group](images/new-group.png "Add new group")

1. Enter a name for the new group and select its parent group. Groups in AC are formatted in a parent-child tree structure.
1. From the left column, select the applications you want to be available to the group users. Click __Add selected__ and the selected applications will be displayed under __Active applications__ section. To remove an application, click the application and then click **Remove Selected**.
1. By default, every group has a list of restricted URLs. To allow restricted URLs, click the URLs and then click **Add Selected**. The URLs move to **Allowed Privileged URLs** and users within the Group can access the URLs. You can hold **Ctrl** on your keyboard to select multiple URLs at once.
1. Every group also has a list of default **Blocked Elements**. To unblock elements, click the elements and then click **Add Selected**. The elements move to the **Unblocked Elements** list. You can hold **Ctrl** on your keyboard to select multiple elements at once.
1. Click **Create** to add the new Group.

>**Caution**: If an LDAP service is running, this may create inconsistencies in the current organization schema.

## Set Global Options

To set global Access Control options, click __Global Options__ in the top right corner of the main panel.

![global](images/global-op.png "Global options")

### Set Master Password

If enabled, Access Controller users can login to organization applications through the Browser Extension (BE). During BE installation they are prompted to enter a personal master password for extra security and for use when basic authentication policy fails (See Enable fallback to master password for more info).

You are able to set a global master password for every organization user by checking the box and entering the desired password in the text fields below .

![mpw](images/mpw.png "Enable master password")

### Set Email Alias

In the text field shown enter an email address that will receive every kind of notification and alert emails regarding your Access Control. Organization admins will stop receiving these emails, if an email alias is set.

### Duo Integration

If enabled, users can authenticate using the DUO app.

![duo](images/duo.png "Enable Duo integration")

### PingID Integration

If enabled, users can authenticate using PingID.

![ping](images/ping-id.png "Enable PingID integration")

## View Group Data
  
![groups data](images/groups.png "Group Data Table")

The Group Data table contains all organization groups. In the first two columns you can see the name of the group __User Group__ and its parent __Parent Group__.

Click __View Group Applications__ to view a list of the available applications for this group.

### Edit Group

If you wish to edit a group click the edit icon under __Actions__ column. 
 
![edit group](images/edit-gr.png "Edit Group")
  
You are now able to change the group’s name and the parent group it belongs to, add or remove active applications, allow or restrict URLs and block or unblock elements according to the group access management that fit your needs. Remember to click __Update__ for changes to take effect.

__Copy__ or __Delete__ a group by clicking on the respective buttons.

>**Caution**: You have to be very careful when delete a group. All of its subgroups will be deleted. This operation cannot be undone. Consider moving the subgroups before continuing. Also, if an LDAP service is running, it might cause inconsistencies.
