[title]: # (AWS Requirements)
[tags]: # (cloud access controller)
[priority]: # (110)
# AWS Private Deployment Requirements**

Cloud Access Controller is part of a Privileged Account Management (PAM) solution. Cloud Access Controller can be
deployed in three ways for installation and use. (1) Completely SaaS offering (2) Private cloud deployment and (3) On premise deployment. This document describes the requirements for a potential customer to deploy Cloud Access controller as a private AWS installation.

## Why AWS VPC

A private installation of Cloud Access Controller inside your own AWS account is very desirable. This deployment model provides you with full control over the access control service at the same time enjoying the benefits of a SaaS offering. For enterprise customers who value data privacy and must comply with stringent compliance, regulatory requirements will find this option attractive. Cloud Access Controller is also available as a completely SaaS solution or as a completely on premise deployment.

## Benefits

* __Data Privacy__: Cloud Access Controller has no access to your data stored on your personal AWS cluster.
* __No change to Internet traffic policies__: No need to make changes to your firewall configurations to open any ports or whitelist any incoming IP ranges.
* __Easy Load Balancing__: Usage of AWS allows you access to features such as elastic load balancing, and high availability architectures already built into AWS.

## Some Considerations

Cloud Access Controller will share AMIs with the customer, and the customer can then follow instructions provided to install the AMIs in their account and configure them appropriately. As an option (for an extra fee) Cloud Access Controller can install the entire system in the customer’s AWS account.

## List of Personnel Involved

1 DevOps person (network setup, AMI installation) and 1 IT person (AD/LDAP integration). Amount of time for the entire AWS installation and setup process is usually less than 3-4 calendar days. For a faster turnaround customers can choose Cloud Access Controller’s hands on installation process for an extra fee.

## List of Equipment and Accounts Required

* Customer AWS account information with whom AMIs can be shared.
* Access to AWS account, if customer decides to have Cloud Access Controller perform the entire installation.
* Permission to provision a minimum of 4 EC2 instances, and utilize AWS RDS, SQS services.
* Cloud Access Controller will provide an agent that will need to be configured on the AD/LDAP forest head.
* Customer needs to purchase SSL (standard or EV) certificates for the AWS installation.

## Installation Guidelines

To smoothly finish the installation, we suggest that the entire process should be done in two phases.

* __Phase 1__

  * Communicate with Cloud Access Controller and provide AWS account access details (email of AWS account)
  * Accept incoming AWS AMI images from Cloud Access Controller, follow instructions in set up manual
  * Configure DNS, mail server information and AD connectivity information
  * Test that the setup works as expected

* __Phase 2__

  * Utilize AWS ELB for auto load balancing
  * Utilize AWS Multi Zone support for HA and failover
  * Utilize AWS Cloud trail for logging and alerting

## Details

The Cloud Access Controller AWS deployment will include several AMIs that need to be installed in your VPC. Cloud Access Controller will provide easy to use Cloud formation templates that will help you launch the installation painlessly. These AMIs include:

__Router AMI__ – This AMI is used to route new user registrations for the browser extension, mobile phone applications to the local and on premise versions of Cloud Access Controller and prevent the mobile device and browser extension from communicating with the SaaS service of Cloud Access Controller.

__Management AMI__ – This AMI is meant to be used as a bastion server which can allow access to the other AMIs over SSH for debugging purposes. Other AMIs do not accept incoming SSH connections directly from any other source except the management AMI.

__Panel AMI__ – This AMI hosts the Cloud Access Controller dashboard and API endpoints.

__Piper AMI__ – This AMI hosts the Cloud Access Controller SSH proxy service.

__RDP AMI__ – This AMI hosts the Cloud Access Controller RDP proxy service.

__WinProxy AMI__ – This AMI is a Windows VM that is used to communicate with and set up various parameters on Windows target servers that need to be protected by Cloud Access Controller.
