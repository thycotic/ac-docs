[title]: # (Policies)
[tags]: # (thycotic access control)
[priority]: # (4)
# Policies

## Application Policies - General Policy

![policy details](images/app-pol.png "Application Policies details")

Thycotic Access Control supports six authentication methods:

* Fingerprint (TouchID): Authenticates users by their fingerprint (applies only to iPhones 5S and later).
* AirShake: Establishes the presence of the user by requiring users to shake their phone.
* Geofencing: Validates that users are within a predefined geological area.
* Geoproximity & Geofencing: Uses the location of the phone to verify that users are next to their computer.
* MasterPass: Requires that users provide a password to their browser extension.
* YubiKey: A YubiKey is a small USB device that offers 2FA by generating one-time passwords.

A Policy consists of:

* Affected Apps and Servers - List of apps and servers that have this policy enabled.
* An Authentication Technique - Combination of up to three authentication methods.
* Supporting Browsers and Operating Systems.
* Include IPs - Thycotic Authentication will be available only from these IPs.
* Exclude IPs - Thycotic Authentication will be forbidden from these IPs.

To configure policies that can be assigned to an application, refer to [Set Policy for Application](../applications/cfg.md#set_policy_for_application).

Under __Policy image__, displayed icons identify the authentication method(s) required by this policy.  
By clicking __Details__ assigned to each policy under the Apps, Users, or Servers Affected columns, you are able to take a quick look at every application, user or server that is affected by this policy at the moment.

### Create an Application Policy

Every organization has default policies available, Fingerprint (TouchID), Geofencing, and Geoproximity & Geofencing.

To create a new policy:

1. Click __Add New Policy__ in the top right corner of the main panel.

   ![new policy](images/add-new-pol.png "Add a new policy")
1. On the __Add new policy__ modal:

   * Enter the new policy name.
   * Select any application or server that will be affected by this policy. You can leave these two fields blank and set the application policy later from the applications’ configuration panel. Refer to [Set Policy for Application](../applications/cfg.md#set_policy_for_application) for instructions.

>**Note**: You must set an Authentication Technique for the new policy. Click on the dropdown menus and select at least three desired methods for this policy.

Use the scroll bar to scroll through the whole __Add New Policy__ modal and set any other configurations you may require.

### Enable Fallback to Master Password

If __Enable Fallback__ is selected, an employee who cannot use their phone to prove their identity and satisfy the policy requirements will be given the option to enter a master password. The employee chooses their master password during the initial registration process. The employee can change it at any time to a different value.

### Enable Auto-login for Specific IP Addresses

Auto-login allows users to log into corporate applications and servers directly from trusted IP locations.

If a user tries to connect to an application from a different IP, Thycotic will use an extra authentication mechanism to verify the user. 
_Example: If auto-login is enabled for a policy that has Geofencing and Touch ID (fingerprint) as authentication methods and a user tries to login to an application from an IP not listed in the IP list, the users will be verified by their location (Geofencing) and fingerprint (Touch ID)._

The 'Included IP' list allows logins only from the IPs included on the list. You can set Browsers, Operating Systems and include/exclude IPs fields according to your needs.

Click __Create Policy__ for your settings to take effect.

## Policy Success Rate

The Policy Success Rate graph shows the most common policies and provides detailed statistics for the number of successful and failed attempts for each policy. You can modify your policies according to the supplied data.

![policy success](images/pol-success.png "Policy success rate chart")

## Time Series Login

The Time Series Login chart shows the number of daily performed login attempts per authentication method.

![time series](images/time-series.png "Time series login chart")
