[title]: # (Introduction)
[tags]: # (thycotic access control)
[priority]: # (1)
# Introduction to Thycotic Access Control

Thycotic's Access Control solution provides access management for

- cloud platforms, via the __Cloud Access Controller__.
- databases, via the __Database Access Controller__.
- remote locations, via the __Remote Access Controller__.

Basically cloud-based SaaS security solutions that give organizations the ability to control access across all their properties.

This documentation provides information pertaining to privilege managed access technology utilizing Thycotic's Access Controllers and how any of the access controller products can secure your infrastructure in specific areas and as an integrated multi-product solution.

* Infrastructure Access Management - Makes sure that only employees get access to organizations´ Cloud Servers and Containers. With a zero software agent approach no server modifications are needed.
* Dynamic Privilege Management - Helps organizations to easily specify which employee can access what on a website or server. Each action is risk scored using machine learning to detect and prevent threats. Policy setup is easy, flexible and no server or website changes are needed.
* Activity Monitoring - Organizations can easily find out which servers, applications and websites employees are using, as well as have access to detailed reports on alerts and invalid actions. With employee session recording, time to compile forensic and compliance reports is considerably reduced.
* License Management - Organizations can get detailed reports on how well their employees are utilizing money spent on cloud services and identify accounts that are not used. Organizations can reduce their threat risk profile and costs.
* Invisible Identity Verification - Helps employees get access to what they need without putting up roadblocks. Two Factor Authentication can be a nuisance. There is no need for 8 digit code login and no hardware to carry. With multiple choices like Geofencing, Geoproximity, AirShake, and Touch ID, the access control solution conveniently merges security and usability.
* User Management - With automatic password resets and LDAP/AD integration, the access control solution makes life easier by integrating with organization´s central directory to maintain a single source of truth. Templates help to automatically create user accounts for new employees and disable accounts for the ones that are no longer employed.

## Overview

Thycotic's Access Controller is a Privileged Access Management (PAM) Solution, providing a single pane of glass from which to control directory management, perform privilege management, specify multi-factor authentication policies and control employee identities. The solution is a cloud based all in one dashboard that helps IT, Security, Compliance administrators get complete control over login policies for websites, servers and applications, inside and outside the organization.

The Access Controller is unlike other PAM products - security should not come at the cost of ease of use, access control melds these both in one cohesive experience. Thycotic's Access Controller is a true PAM As A Service offering.

How does it help an organization: Thycotic's Access Controller allows an organization to implement login policies quickly, in less than 5 minutes. The service allows the organization to tightly control access to company resources, without spending months on developer effort and complicated API integration. Thycotic Access Control elevates the security posture for an organization and helps users and admins save time, and stop responding to login related inquiries.

Who is Thycotic's Access Controller meant for: It is meant to be used by IT admins, devops teams to manage employee logins, rights and access. The IT admins and devops teams manage and control login policies, and can quickly increase the overall security in the team. The end users are employees of the organization spanning sales, marketing, HR, Legal and other work functions.

High Level Objectives of the product: 

1. Allow admins to stop or reduce password use in the organization.
1. Allow access to internal and 3rd party apps and websites to be tightly controlled.
1. Allow infrastructure like servers, AWS instances and more to be part of the access control policies.
1. Reduce user friction when employing Two Factor Authentication.
1. Provide actionable alerts, robust reporting for all authentication related issues in the organization.

Typical Workflow (for full product): An Admin of an organization is provisioned with an account at the Access Control panel. The admin visits a access control panel URL, and gets access to the dashboard for his organization. The dashboard allows the admin to view what applications are registered by the organization. The admin can also add applications by just specifying the login URL(s) for the 3rd party service. Then the admin can import a user database from an LDAP/AD store, excel sheets, CSV files. Each user gets an invitation via email about their participation in the program. Each user will be directed to download appropriate browser extensions and cell phone application.

When an end user, employee of the organization visits a website for the first time after the Access Controller browser extension installation, they are asked for the username and password by the browser extension and when received as input from the user, are stored and transmitted to the cloud backend. When the user needs to be logged into the site, the cloud backend retrieves the decrypted information from the vault and provides credentials to the website in question in an automated manner. This helps simplify the login experience for end users and removes the burden of password management. The Thycotic Access Controller allows the admins to specify rules and policies for login access, such as: geo fencing, geo proximity, TouchID and more. This allows for a low friction Two Factor Authentication (2FA) as opposed to high user friction techniques as OTP, carrying hardware and others. Thycotic Access Control makes 2FA near invisible.

The Thycotic Access Controller never stores credentials on your laptop, thereby defeating malware that may try to use key logging software. The access controller only transfers encrypted credentials to the user’s browser. The Thycotic Access Controller allows for admins to get fine grained access for privilege management on websites that users would be visiting. The access controller also allows for the protection of SSH, RDP access to server pools by providing a transparent SSH, RDP proxy to check for user-server policies and then enforcing them. If the policy is satisfied (e.g. dev abcd should use TouchID when pushing code to server group X) the SSH, RDP connection is allowed through.

If a user’s computer is stolen, or infected with malware, simple password managers may happily fill in login forms and thereby compromise user accounts. The Thycotic Access Control solution  implements mandatory 2FA to prevent this from happening. Further, the Thycotic Access Controller has the ability to refresh passwords on websites according to the frequency specified by the admin. End consumer centric products have no concept of privilege management and real time alerting for business critical accounts.
