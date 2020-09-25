[title]: # (Introduction)
[tags]: # (thycotic access control)
[priority]: # (1)
# Introduction to Thycotic Access Controller

Thycotic's Access Controllers are cloud-based SaaS security solutions that enable your organization to govern access to digital properties.

Thycotic offers:

- __Cloud Access Controller__ - for managing access to cloud platforms.
- __Database Access Controller__ - for managing access to databases.
- __Remote Access Controller__ - for managing access from remote locations.

This documentation provides an overview of how Thycotic's Access Controllers can secure your infrastructure either in specific areas or as an integrated multi-product solution.

## Key Features

* __Infrastructure Access Management__ - Certifies that only employees get access to organizations´ Cloud Servers and Containers. With a zero software agent approach, no server modifications are needed.
* __Dynamic Privilege Management__ - Allows your organization to easily specify what an individual employee can access on a specific website or server. Each action taken is risk-scored using machine learning to detect and prevent threats. Policy setup is easy, flexible and no server or website changes are needed.
* __Activity Monitoring__ - Your organization can easily identify which servers, applications, and websites employees are using. They will then have access to detailed reports on alerts and invalid actions. With employee session recording, the time to compile forensic and compliance reports is considerably reduced.
* __License Management__ - You will get detailed reports on how well employees are utilizing money spent on cloud services and identify accounts that are not used. Your organization can reduce your threat risk profile and costs.
* __Invisible Identity Verification__ - Helps employees get access to needed resources without putting up roadblocks. Verification methods such as two factor authentication, 8 digit code logins, and hardware-based digital keys can be a time and money wasting nuisance. With multiple options like Geofencing, Geoproximity, AirShake, and Touch ID, the access control solution conveniently merges security and usability.
* __User Management__ - With automatic password resets and LDAP/AD integration, the access control solution makes life easier by integrating with your organization´s central directory to maintain a single source of truth. Templates help to automatically create user accounts for new employees and disable accounts for the ones that are no longer employed.

## Overview

### Product

Thycotic's Access Controller is a true Privileged Access Management (PAM) as a Service offering. Unlike other PAM products that sacrifice ease-of-use for security, Access Controller combines security and usability into one cohesive experience.

Thycotic's Access Controller is a PAM Solution providing a powerful command center that allows you to control directory management, perform privilege management, specify multi-factor authentication policies, and control employee identities. The solution comes as a cloud based, all-in-one dashboard that gives IT, security, and compliance administrators complete control over login policies for websites, servers, and applications both inside and outside of the organization.

### Implementation

Thycotic's Access Controller allows your organization to implement login policies with incredible speed. The service affords you tight control of access to company resources without spending time and money on unnecessary developer effort and complicated API integration. Thycotic Access Control elevates the security posture for your organization. It saves time for your employees and removes the need for your administrators to respond to login-related inquiries.

### Use

Access Controllers are used by IT administrators and devops teams to manage employee logins, rights and access. The admins and teams can quickly increase the overall security of the team by managing and controlling login policies. The end users are employees of your organization spanning sales, marketing, HR, legal, and any other role that requires access to digital properties.

## High Level Objectives

* Stop or reduce reliance on passwords.
* Tightly control access to both internal and 3rd party apps and websites.
* Apply access control policies to critical infrastructure like servers and AWS instances.
* Reduce user friction when employing Two Factor Authentication.
* Provide actionable alerts and robust reporting for all authentication-related issues.

## Typical Workflow

### Administrator Set-Up
An administrator of your organization is provisioned with an account. The admin then visits the Access Control panel URL and gains access to your organization's Access Controller Dashboard. The dashboard allows the admin to view the applications that are registered by the organization. The admin can also add applications by simply specifying the login URL(s) for the 3rd party service. The admin then imports a user database from an LDAP/AD store, excel sheet, or CSV file.

The admin then specifies rules and policies for login access. Options include: geo fencing, geo proximity, and TouchID. This allows for low friction, nearly invisible Two Factor Authentication (2FA) free from the inconvenience of traditional roadblocks.

### End-User Set-Up
Each user gets an invitation to participate in the program via email. Once accepted, the users will be directed to download the browser extensions and cell phone applications. When your employee visits a website for the first time after installing the Access Controller browser extension, they are prompted to provide a username and password. This secret is then stored and transmitted to the cloud backend. When the user needs to log into a site, the cloud backend retrieves the decrypted information from the vault, verifies the user's identity, and automatically provides credentials to the website. This simplifies the login experience for end users and removes the burden and risk of password management.

### Admin-User Experience
The Thycotic Access Controller __never__ stores credentials on local machines, thereby eliminating the risk of key-logging attacks. The access controller only transfers encrypted credentials to the user’s browser. The Thycotic Access Controller gives fine-grained access for privilege management on websites that users visit. The access controller also protects SSH and RDP access to server pools by providing transparent SSH and RDP proxies to check for user-server policies and enforce them. If the policy is satisfied using invisible 2FA, the SSH or RDP connection is allowed.

If an employee's machine is compromised, a traditional password manager will give a malicious actor access to your organization's digital properties. The Thycotic Access Control solution implements mandatory, unobtrusive, and secure 2FA to prevent these threats. For further security, the Thycotic Access Controller allows admins to set intervals for refreshing website passwords.
