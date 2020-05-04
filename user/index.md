[title]: # (End User)
[tags]: # (thycotic access control)
[priority]: # (1001)
# End User's Guide

This document provides a brief overview of Thycotic's Access Control solution and acts as a user guide for the product. This document is meant for employees of the organization that is employing Thycotic Access Control to manage privileges for user and administrative accounts.

Thycotic Access Control is a Privileged Access Management (PAM) Solution. providing
a single pane of glass from which to control directory management, perform privilege management,
specify multi-factor authentication policies and control employee identities. The solution is a cloud based all in one dashboard that helps IT, Security, Compliance administrators get complete control over login policies for websites, servers and applications, inside and outside the organization.

OID is unlike other PAM products - security should not come at the cost of ease of use, OID melds
these both in one cohesive experience. OID is a true PAM As A Service offering.

How does it help an organization: OID allows an organization to implement login policies quickly, in
less than 5 minutes. The service allows the organization to tightly control access to company
resources, without spending months on developer effort and complicated API integration. OID
elevates the security posture for an organization and helps users and admins save time, and stop
responding to login related inquiries.

Who is Onion ID meant for: OID is meant to be used by IT admins, devops teams to manage
employee logins, rights and access. The IT admins and devops teams manage and control login
policies, and can quickly increase the overall security in the team. The end users are employees of the
organization spanning sales, marketing, HR, Legal and other work functions.

High Level Objectives of the product: (1) Allow admins to stop or reduce password use in the
organization. (2) Allow access to internal and 3rd party apps and websites to be tightly controlled. (3)
Allow infrastructure like servers, AWS instances and more to be part of the access control policies. (4)
Reduce user friction when employing Two Factor Authentication. (5) Provide actionable alerts, robust
reporting for all authentication related issues in the organization.

Typical Workflow (for full product): An Admin of an organization is provisioned with an account at
OID. The admin visits a OID URL, and gets access to the OID dashboard. The dashboard allows the
admin to view what applications are registered by the organization. The admin can also add
applications by just specifying the login URL(s) for the 3rd party service. Then the admin can import a
user database from an LDAP/AD store, excel sheets, CSV files. Each user gets an invitation via email
about their participation in the OID program. Each user will be directed to download appropriate
browser extensions and cell phone application.
When an end user, employee of the organization visits a website for the first time after OID browser
extension installation, they are asked for the username and password by the browser extension and
when received as input from the user, are stored and transmitted to the OID cloud backend. When the
user needs to be logged into the site, the cloud backend retrieves the decrypted information from the
Onion ID vault and provides credentials to the website in question in an automated manner. This helps
simplify the login experience for end users and removes the burden of password management. OID
allows the admins to specify rules and policies for login access, such as: geo fencing, geo proximity,
TouchID and more. This allows for a low friction Two Factor Authentication (2FA) as opposed to high
user friction techniques as OTP, carrying hardware and others. OID makes 2FA near invisible.

How is it better than consumer centric password managers (LastPass): OID never stores
credentials on your laptop, thereby defeating malware that may try to use key logging software. OID
only transfers encrypted credentials to the user’s browser. OID allows for admins to get fine grained
access for privilege management on websites that users would be visiting. OID also allows for the
protection of SSH, RDP access to server pools by providing a transparent SSH, RDP proxy to check for
user-server policies and then enforcing them. If the policy is satisfied (e.g. dev abcd should use
TouchID when pushing code to server group X) the SSH, RDP connection is allowed through.

If a user’s computer is stolen, or infected with malware, simple password managers may happily fill in
login forms and thereby compromise user accounts. OID will implement mandatory 2FA to prevent
this from happening. Further, OID has the ability to refresh passwords on websites according to the
frequency specified by the admin. End consumer centric products like LastPass have no concept of
privilege management and real time alerting for business critical accounts.
