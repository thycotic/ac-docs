Onion ID On-Premise Deployment Guide

**Confidential – Not for Distribution**

**DOWNLOAD** 
=============

Onion ID (OID) provides two (2) Virtual machine images. The first one (Linux
based) contains the majority of the functionality of the Onion ID solution. The
second one (Windows based) is specific to managing privileges on Windows
machines. If your organization is not planning to use or manage Windows servers,
the second image does not need to be installed.

**Login URL:**  <https://onionid.signin.aws.amazon.com/console>

>   **Account:** onionid-prod

>   **Username:** onprem

>   **Password:** Vcn07DvIv1

The images are located under:

**S3 -\> oid-onprem-artifacts -\> vmware -\> v1.X**

*Linux instance* Onionid-v1.X.ova

*Windows instance* WinProxy-v1.X.ova

**DEPLOYMENT** 
===============

For the PoC we recommend the following specs for VMs:

>   **ESXi version:** \>= 5.5

>   **Linux**: 128 GB storage and 16 GB RAM

>   **Windows:** 128 GB storage and 16 GB RAM

For the PoC deployments Onion ID does not implement any HA functionality. The
customer should first verify that all product features are acceptable and
following that when the PoC is determined to be successful Onion ID will present
a deployment plan specific to the customer’s environment.

**INITIAL SETUP**
=================

**Credentials for Linux instance:**

**Username**: root

**Password**: m0ld\@stat1oN

**Credentials for Windows instance:**

**Username:** Administrator

**Password:** 4&tg3pg(qw

NETWORK
-------

The ports that need to be open per image are the following:

-   **Inbound** TCP ports:

    -   *Linux*: 80, 443, 4443, 2222, 22

    -   *WinProxy*: 2222, 3389

-   **Outbound** TCP ports:

    -   *Linux*: all

    -   *WinProxy*: all

Please let your Onion ID account representative know if opening outbound traffic
for all ports is not possible. This will limit the amount of functionality you
can receive from the Onion ID system.

CERTIFICATES
------------

Onion ID comes with pre-configured SSL certificates for \*.onionid.net, which
you are free to use for the PoC. However, we **highly recommend that you install
your own signed certificates.**

If other SSL certificates need to be installed on the Linux instance, they
should be **manually uploaded and configured**. Please make sure you install
certificates **from a trusted CA** for the domains you set up above.

You should install your certificates on the Linux box as follows:

**Private key location:**

/etc/ssl/private/\<YOUR_KEY_NAME\>.key

**Permissions:**

>   *Ownership*: root:ssl-cert

>   *File permissions*: 0640

Public crt (and bundle file, if it exists) should go in the following directory:

/etc/ssl/certs/\<YOUR_CRT_FILE\>.crt

/ect/ssl/certs/\<YOUR_CA_BUNDLE_FILE\>.ca-bundle

Configure SSL in the **apache** virtual hosts in:

/etc/apache2/sites-available/000-default.conf

/etc/apache2/sites-available/rdp.conf

Configure SSL in the **nginx** virtual hosts in:

/etc/nginx/sites-available/default

In order to properly configure SSL for nginx in the above file, you need to set
the **ssl_certificate** directive to the **chained SSL certificates**, otherwise
you may encounter SSL certificate issues[^1].

[^1]: http://nginx.org/en/docs/http/configuring_https_servers.html\#chains

To generate the chain SSL certificate, an example command would be the following
(depending on your SSL certificate provider this may differ):

\$ cat example.com.crt bundle.crt \> example.com.chained.crt

DNS
---

Set proper DNS records for the instances. 2 records are required for the Linux
instance and 1 for the Windows instance.

If at section 3.2 above you decided to **use your own signed wildcard
certificates** (e.g. \*.organization.com), then the DNS records should be like
the examples below.

-   **Linux** Instance

    -   **oid-panel.ORGANIZATION.com** resolving to the IP of the Linux instance

    -   **oid-rdp.ORGANIZATION.com** resolving to the IP of the Linux instance

-   **Windows** Instance

    -   **oid-winproxy.ORGANIZATION.com **resolving to the IP of the Windows
        instance

If you decided to **keep the Onion ID signed wildcard certificates**, then the
DNS records should be like the examples below:

-   **Linux** Instance

    -   **organization-panel.onionid.net** resolving to the IP of the Linux
        instance

    -   **organization-rdp.onionid.net** resolving to the IP of the Linux
        instance

-   **Windows** Instance

    -   **organization-winproxy.onionid.net **resolving to the IP of the Windows
        instance

sOnion ID connects to a limited set of, well known, 3rd party services such as:
Twilio for SMS notifications, IP-API for geolocation services, Duo for 2FA
(optional), Yubico for 2FA (optional), Okta for user sync (optional) and SSO.

Also, please keep in mind that the Onion ID setup without the above inbound
ports open will affect how 2FA is done with the Onion ID mobile application.
Alternatively, you may use Duo (optional) or Yubikey for 2FA (optional).

1.  **CONFIGURATION**

    1.  SETUP SCRIPT

2.  Log into the Linux instance (as **root**)

3.  Run the setup wizard:

\$ cd

\$ ./setup.sh

1.  Choose **'s' for setup.**

2.  Set the appropriate values:

-   DNS names assigned previously

-   HTTP vs HTTPs\*

-   Enter the **mail server** information:

    -   Mail server **hostname**

    -   **Credentials** for mail server (if required)

    -   **PORT** number

    -   Whether it uses **TLS** or not

In case of error, please re-run the setup wizard. If you continue to face issues
please provide your Onion ID account representative with information from your
syslog to be able to debug quickly.

**\*IMPORTANT**: If the **SSL** termination happens on an **ELB**, you need to
answer ‘**no**’ when the wizard asks for the HTTPs parameter. ELB is only
applicable when the Onion ID images are being installed in an AWS account.

CREATE YOUR ORGANIZATION
------------------------

Switch to the **OnionID** user and create an initial organization:

\$ su – onionid

\$ cd \~onionid/panel

\$ php artisan organization:create ORGNAME --username UNAME --email EMAIL --plan
Enterprise --expire no

If an error occurs (i.e. mail configuration is not correct), you can revert the
above:

\$ php artisan organization:purge ORGNAME

ACCESS ONION ID PANEL 
----------------------

When the organization was created successfully, an email with first-time login
instructions for the OID panel will go to the EMAIL defined above. Access the
Onion ID dashboard to continue the initial registration through your browser:

https://*oid-panel.ORGANIZATION.com*
