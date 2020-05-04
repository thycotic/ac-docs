[title]: # (Authentication Overview)
[tags]: # (cloud access controller)
[priority]: # (200)
# Authentication Overview

Cloud Access Controller is a single pane of glass to provide security, visibility and auditing
for any enterprise. Cloud Access Controller’s flexible and powerful solution provides you with
the power of choice. Enterprises select how much security is right for them and how they want to implement it. This document describes the authentication, authorization and auditing workflows that customers can employ using Cloud Access Controller.

Cloud Access Controller respects privacy for all customer data and secures all information
related to customer usage of applications and servers. Security is of paramount
concern to us.

## Why Cloud Access Controller

Using Cloud Access Controller means never having to worry about passwords, resetting them,
choosing a new one or having a piece of malware record your login details. Cloud Access Controller protects all your online accounts and your servers. The setup process is easy and you will not have to worry about account security ever again.

## Layers of Security

Cloud Access Controller makes sure that your credentials are stored securely and encrypted in
order to protect the data. Cloud Access Controller stores information like passwords,
usernames, token information by encrypting each piece separately, with unique
keys for every piece. This makes our secure storage exponentially strong as
multiple pieces of information are stored in a segregated manner. This strategy
ensures that user accounts do not share any encryption keys.

## Firewalls

Cloud Access Controller uses firewall rules to make sure only specific traffic can reach its
internal servers. Cloud Access Controller has employed a specific set of IP addresses that are
carefully controlled and monitored to prevent any external system from
connecting to internal servers.

## Encryption

Cloud Access Controller takes encryption seriously. Every communication to and from Cloud Access Controller is
secured by encryption. All data stored for customers is encrypted. Cloud Access Controller
makes sure that keys for servers get rotated regularly and that its own systems
are regularly tested. Cloud Access Controller uses:

* Encryption algorithm for passwords: AES256.

* Hashing: sha256 (salted).

* Key lengths: 32 bytes (uses openSSL for randomness and other crypto ops).

* Keys are created per password (different keys for different accounts, even
    for the same user).

* Keys are stored in a separated database, completely isolated. It uses its
    own data encryption as well [1].  

Source:
[1] <http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.html>
