[title]: # (Security Overview)
[tags]: # (thycotic access control)
[priority]: # (201)
# Internal Security Posture

Enterprises select how much security is right for them and how they want to implement it. This document describes the measure taken by Thycotic to protect your information.

Thycotic respects privacy for all customer data and secures all information related to customer usage of applications and servers. Security is of paramount concern to us.

## Why Onion ID

Using Onion ID means never having to worry about passwords, resetting them, choosing a new one or having a piece of malware record you login details. Onion ID protects all your online accounts and your servers. The set up process is easy and you will not have to worry about account security ever again.

## Layers of Security

Onion ID makes sure that your login information is stored securely, layered with various biometric technologies to protect it. Onion ID stores Login information like passwords, usernames, token information by encrypting each piece separately, with different un-guessable salts and unique keys for every piece. This makes our secure storage exponentially strong as multiple pieces of information are stored in a segregated manner. This strategy ensures that all login credentials do not share any encryption keys.

## Firewalls

Onion ID uses firewalls to make sure only specific traffic can reach its servers. Onion ID has employed a specific set of IP addresses that are carefully controlled and monitored to prevent any external system from connecting to internal servers.

## Containerized Architecture

Onion ID takes security to the next level by making sure that different types of customer data is stored on separate clusters of servers. Each cluster is earmarked for one single purpose and does not intermingle different pieces of data together. This allows for tight control over server access and avoids any data co-mingling.

## Encryption

Onion ID takes encryption seriously. Every communication to and from Onion ID is secured by encryption. All data stored for customers is encrypted. Onion ID makes sure that keys for servers get rotated regularly and that its own systems are regularly tested. Onion ID uses:

* Encryption algorithm for passwords: AES256.
* Hashing: sha256 (salted).
* Key lengths: 32 bytes (uses openSSL for randomness and other crypto ops).
* Keys are created per password (different keys for different accounts, even
    for the same user).
* Keys are stored in a separated database, completely isolated. It uses its own data encryption as well, refer to http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.html.  
