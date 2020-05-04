[title]: # (Best Practices - Migration)
[tags]: # (cloud access controller)
[priority]: # (202)
# Best Practices for Migration from Legacy PAM

Here we list a brief workflow for an easy off-boarding from an existing PAM legacy solution to Cloud Access Controller.

1. Please visit the password vault area of your existing PAM solution and ascertain if there is a way to export out usernames (usually root), IP or DNS information and passwords for the servers you want to migrate to Onion ID.
1. Please export out if possible in a CSV format and make sure the file is text format based.
1. Please use a command line language like awk, grep, shell or languages like Perl that are friendly for text processing and make sure that you have 3 pieces of information on every line of the CSV: IP/DNS of server, Account login (root), password. Hint: You can name (key-name) your secret as a combination of the IP/DNS and account, e.g. key-name for a secret can be 192.168.0.1-root .
1. Use the Cloud Access Controller API (examples below) to upload the information as separate “secrets” in the Cloud Access Controller secret storage area.

## GET /secret/{key}

Returns the value of the secret.

Sample response:

```rest
{
"status": "success",
"key": "key-name",
"secret": "Secret message."
}
```

## GET /secrets/list

Returns a list of the keys corresponding to the stored secrets.
  
Sample response:

```Rest API
{
"status": "success",
"secret_keys": [
"first",
"third",
"fourth",
"second"
]
}
```

## POST /secret/store

Stores a new secret in the storage.
  
Sample request body:

```rest
{
"type" : "generic", // **Will be extended for 'aws' and more**
"key": "key-name",
"value": "This is a secret."
}
```

## POST /secret/delete

Deletes a secret from storage.
  
Sample request body:

```rest
{
"key": "key-name" // The key of the secret you want to delete
}
```

## POST /secret/{key}/share

Share a secret with other members of your organisation  
  
Sample request body:

```rest
{
"users": \<array of e-mail addresses\> //for example
["<user1@myserver.com>", "<user2@myserver.com>"]
}
```

Once the root passwords have been uploaded into Cloud Access Controller, you can use the Cloud Access Controller API to upload a list of servers directly to Cloud Access Controller. Cloud Access  Controller will set the SSH keys for the root users automatically, as described in the previous section. The secret storage area should only be used if someone absolutely needs access to the root password. In the general scheme of things, employees should always be “mapped” to the account on the server they need to access but should not be provided with the root password for the server. For a quick tutorial please view this - https://youtu.be/zoxykeDRWrU

If you require any assistance or clarifications about the API calls mentioned here, please contact your Cloud Access Controller representative for sample scripts and information.
