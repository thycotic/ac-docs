[title]: # (Mobile Registration)
[tags]: # (registration)
[priority]: # (3)
# Mobile Device Registration

After a successful [Browser Extension](be.md) installation and registration, follow the link in your registration email, to download the OnionID (Thycotic Access Controller) Application.

![email 2](images/mobile-email.png "Email prompting to download the mobile app for device registration")

After installing the OnionID (Thycotic Access Controller) Application from your devices app store, follow these registration steps:

1. Open the newly installed mobile application.
1. The application prompts you for your registration code:

   ![reg code mobile](images/mobile-reg-code.png "Mobile app prompting for registration code")

   Use the registration code that was emailed and that you also used in the browser extension registration.

   Click __Submit__.
1. The application prompts to set up a PIN in case TouchID/Fingerprint isn't available or won't work.

   ![pin setup](images/pin.png "Initial PIN setup")

   Enter a 4-digit PIN and Click __Ok__.
1. Back at your computer, if you are currently logged into the panel, logout and reload the login page. Users that have not accessed the panel, open the login URL.
1. In the register modal, provide your user email and password, click __Register__.

   ![register](images/register-1.png "Register the user account with the mobile app for authentication")

You mobile device is now registered and ready to be used for subsequent logins.

## Using Mobile Authentication

After you successfully registered your user account the your mobile device app, every login into the access controller panel will now authenticate via your mobile app.

1. Navigate to the Access Controller URL and open the panel login page.

   ![login](../getting-started/images/login.png "Open the login page")

   The pending authentication modal opens up:

   ![pending pc](images/pending-pc.png "Pending authentication modal")
1. On your mobile device, open the OnionID application. The app displays a pending login attempt:

   ![pending](images/pending.png "Pending login attempt")
1. Click __Authenticate to...__.
1. Either use your Fingerprint or a PIN to authenticate the login. In this example we use a PIN.

   ![pin](images/auth-pending.png "Authentication method prompt")

   Click __PIN__ and enter your authentication pin, click __Submit__.

   On your computer, the panel application opens to the home page.

## Mobile App Settings

The mobile app also lets you change your PIN. Provides an unregister option and in-app browsing of applications that are setup for your company profile. 

### Unregister

Navigate to the mobile app settings via the __gear__ on the main mobile app screen. Select __Unregister__ and confirm that you wish to unregister the mobile application.

![main mobile](images/no-pending.png "Settings gear on main mobile screen, entry point to unregister")

### Change your PIN

To change your mobile app PIN, navigate to the mobile app settings via the __gear__ and select __Change PIN__. You are asked for you old PIN and have to enter the new PIN twice. Click __Submit__ to save the change.

![pin change](images/change-pin.png "Options to change the pin")

### In-app Browsing

You can navigate to a list of applications that are registered through your company's panel. Select the application and associated account to login. Once authenticated you can browse the application from inside the Access Controller mobile app.

![in-app browsing](images/apps-list.png "List of applications available for in-app browsing")
