[title]: # (Applications)
[tags]: # (thycotic access control)
[priority]: # (3)
# Applications

Under Applications, you find the applications that have been made available in your organization's portal. Use the applications area to add, configure, and remove applications.

![applications home](images/applications.png "Applications home page")

To filter application based on state, select the Filter drop-down:

![filter applications](images/cfg-drop-down.png "Filtering applications based on state and category")

## Add an Application

To include an application that is not already on the list of available applications, follow these steps:

1. Select __Applications__ from the left menu.
1. Click __Add Application__.

   ![add app](images/new-app.png "New Application modal")
1. On the __New Application__ modal:

   * Enter the Application URL
   * Enter the Display Name
   * Specify if the application relates to an existing application and/or if the application is internal.
        * If the new application **is related** to an existing application, the application will be instantly added to your panel. _For example: If your application list already contains Salesforce, and you would like to add Salesforce China, use a unique name such as 'Salesforce China' and specify the appropriate URL. Then, indicate that the new application is related to the already existing 'Salesforce' application from the drop-down list. Usage of this option allows you to have different application tiles for different URLs that point to the same application._
        * If the new application **does not relate** to an existing application, Thycotic will receive your request and provision this application to the list of available applications within 24 hours. You will be notified with an email when the app is available in your panel. The application will initially appear as disabled, so you will have to enable it as described in: [Enable/Disable Applications](enable-app.md).
        * If internal application is selected, then the application you have added will only be available for your organization's dashboard. This option should be used for non-public applications that are only accessible from inside your organization.
1. Click __Create__.