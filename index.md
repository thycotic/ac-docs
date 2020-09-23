[title]: # (Introduction)
[tags]: # (thycotic access control)
[priority]: # (1)
# Introduction to Thycotic Access Control

Thycotic's Access Controllers are cloud-based SaaS security solutions that enable your organization to govern access to digital properties.

Thycotic offers:

- __Cloud Access Controller__ - for managing access to cloud platforms.
- __Database Access Controller__ - for managing access to databases.
- __Remote Access Controller__ - for managing access from remote locations.

This documentation provides an overview of how Thycotic's Access Controllers can secure your infrastructure in specific areas or as an integrated multi-product solution.

## Key Features

* __Infrastructure Access Management__ - Certifies that only employees get access to organizations´ Cloud Servers and Containers. With a zero software agent approach, no server modifications are needed.
* __Dynamic Privilege Management__ - Allows your organization to easily specify what an individual employee can access on a specific website or server. Each action taken is risk-scored using machine learning to detect and prevent threats. Policy setup is easy, flexible and no server or website changes are needed.
* __Activity Monitoring__ - Organizations can easily identify which servers, applications, and websites employees are using. They will then have access to detailed reports on alerts and invalid actions. With employee session recording, the time to compile forensic and compliance reports is considerably reduced.
* __License Management__ - Organizations can get detailed reports on how well their employees are utilizing money spent on cloud services and identify accounts that are not used. Organizations can reduce their threat risk profile and costs.
* __Invisible Identity Verification__ - Helps employees get access to needed resources without putting up roadblocks. Verification methods such as two factor authentication, 8 digit code logins, and hardware-based digital keys can be a time and money wasting nuisance. With multiple options like Geofencing, Geoproximity, AirShake, and Touch ID, the access control solution conveniently merges security and usability.
* __User Management__ - With automatic password resets and LDAP/AD integration, the access control solution makes life easier by integrating with organization´s central directory to maintain a single source of truth. Templates help to automatically create user accounts for new employees and disable accounts for the ones that are no longer employed.

## Overview

__Product__

Thycotic's Access Controller is a true PAM As A Service offering. Unlike other PAM products that sacrifice ease-of-use for security, Access Controller combines security and usability into one cohesive experience.

Thycotic's Access Controller is a Privileged Access Management (PAM) Solution providing a powerful command center that allows you to control directory management, perform privilege management, specify multi-factor authentication policies, and control employee identities. The solution comes as a cloud based, all-in-one dashboard that gives IT, security, and compliance administrators complete control over login policies for websites, servers, and applications both inside and outside of the organization.

__Implementation__

Thycotic's Access Controller allows your organization to implement login policies with incredible speed. The service affords you tight control of access to company resources without spending time and money on unnecessary developer effort and complicated API integration. Thycotic Access Control elevates the security posture for your organization. It saves time for your employees and removes the need for your administrators to respond to login-related inquiries.

__Use__

Access Controllers are used by IT administrators and devops teams to manage employee logins, rights and access. The admins and teams can quickly increase the overall security of the team by managing and controlling login policies. The end users are employees of your organization spanning sales, marketing, HR, legal, and any other role that requires access to digital properties.

## High Level Objectives

* Stop or reduce reliance on passwords.
* Tightly control access to both internal and 3rd party apps and websites.
* Apply access control policies to critical infrastructure like servers and AWS instances.
* Reduce user friction when employing Two Factor Authentication.
* Provide actionable alerts and robust reporting for all authentication-related issues.

## Typical Workflow

An Admin of an organization is provisioned with an account at the Access Control panel. The admin visits a access control panel URL, and gets access to the dashboard for his organization. The dashboard allows the admin to view what applications are registered by the organization. The admin can also add applications by just specifying the login URL(s) for the 3rd party service. Then the admin can import a user database from an LDAP/AD store, excel sheets, CSV files. Each user gets an invitation via email about their participation in the program. Each user will be directed to download appropriate browser extensions and cell phone application.

When an end user, employee of the organization visits a website for the first time after the Access Controller browser extension installation, they are asked for the username and password by the browser extension and when received as input from the user, are stored and transmitted to the cloud backend. When the user needs to be logged into the site, the cloud backend retrieves the decrypted information from the vault and provides credentials to the website in question in an automated manner. This helps simplify the login experience for end users and removes the burden of password management. The Thycotic Access Controller allows the admins to specify rules and policies for login access, such as: geo fencing, geo proximity, TouchID and more. This allows for a low friction Two Factor Authentication (2FA) as opposed to high user friction techniques as OTP, carrying hardware and others. Thycotic Access Control makes 2FA near invisible.

The Thycotic Access Controller never stores credentials on your laptop, thereby defeating malware that may try to use key logging software. The access controller only transfers encrypted credentials to the user’s browser. The Thycotic Access Controller allows for admins to get fine grained access for privilege management on websites that users would be visiting. The access controller also allows for the protection of SSH, RDP access to server pools by providing a transparent SSH, RDP proxy to check for user-server policies and then enforcing them. If the policy is satisfied (e.g. dev abcd should use TouchID when pushing code to server group X) the SSH, RDP connection is allowed through.

If a user’s computer is stolen, or infected with malware, simple password managers may happily fill in login forms and thereby compromise user accounts. The Thycotic Access Control solution  implements mandatory 2FA to prevent this from happening. Further, the Thycotic Access Controller has the ability to refresh passwords on websites according to the frequency specified by the admin. End consumer centric products have no concept of privilege management and real time alerting for business critical accounts.
