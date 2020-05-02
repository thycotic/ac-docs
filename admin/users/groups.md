[title]: # (Groups)
[tags]: # (thycotic access control)
[priority]: # (6)
# Create Group

Thycotic Access Control categorizes users into groups based on the available applications and the level of access. Hence, you will probably need to create multiple user groups with certain settings. To do so, click on the __Add Group__ button located at the top right hand corner of the main panel.

![TODO](images/new-group.png "Add new group")

Enter a name for the new group and select its parent group. Remember that groups in the access controller are formatted in a parent - child tree structure.

Then, from the left column, select the applications you want to be available to the group users. Click __Add selected__ and the selected applications will be displayed under __Active applications__ section. Follow the opposite procedure to remove an application from the active applications list. By default, every group has a list of restricted URLs and blocked elements. During group creation, you are able to select any URLs or elements from the corresponding section and add them to the allowed URLs or unblocked elements section respectively. Finally, click __Create__ for changes to take effect.

>**Note**: You are able to edit group settings later as well. For more info check View Group Data section.

>**Caution**: If an LDAP service is running, this may create inconsistencies in the current organization schema.

## Create User

If you wish to create a new user click the __Add User__ button at the top right hand corner of the main panel. From the popup window that comes up, fill in the displayed fields with user’s information such as firstname, lastname, address etc. Then, select a role you want to be assigned to and the group that will belong to. Finally, click __Create User__ for changes to take effect.

>**Caution**: If you assign the role __Admin__ to a user, he will be able to login to the Thycotic Access Control panel. 

## Set Global Options

In order to set global Thycotic Access Control options, click __Global Options__ located at the top right corner of the main panel.

![TODO](images/global-op.png "Global options")

### Set Master Password

Thycotic Access Control users can login to organization applications through the Browser Extension (BE). During BE installation they are requested to enter a personal master password for extra security and for using it when basic authentication policy fails (See Enable fallback to master password for more info).

You are able to set a global master password for every organization user by checking the box and entering the desired password in the text fields below .

![TODO](images/mpw.png "Enable master password")

### Set Email Alias

In the text field shown enter an email address that will receive every kind of notification and alert emails regarding Thycotic Access Control. Organization admins will stop receiving these emails if an email alias is set.

## View Group Data
  
![TODO](images/gr-data.png "Group Data Table")

The Group Data table contains all organization groups. In the first two columns you can see the name of the group __User Group__ and its parent __Parent Group__.

Click __View Group Applications__ to view a list of the available applications for this group.

### Edit Group

If you wish to edit a group click on the button under __Actions__ column. 
 
![TODO](images/edit-gr.png "Edit Group")
  
You are now able to change the group’s name and the parent group it belongs to, add or remove active applications, allow or restrict URLs and block or unblock elements according to the group access management that fit your needs. Remember to click __Update__ for changes to take effect.

Copy or delete a group by clicking on the respective buttons.

>**Caution**: You have to be very careful when delete a group. All of its subgroups will be deleted. This operation cannot be undone. Consider moving the subgroups before continuing. Also, if an LDAP service is running, it might cause inconsistencies.
