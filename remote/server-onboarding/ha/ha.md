[title]: # (High Availability)
[tags]: # (remote access controller)
[priority]: # (2)
# High Availability Setup

In order to perform high availability for the access controller on premise system, we will need to attach an NFS mount on panel instances. This will help us to share the common folders between panel instances, for example session, images, ssh keys and more.

>**Note**: Execute all commands in this tutorial as the root user on the Linux Virtual Machine Image.

## NFS Setup

  1. [Setup a Standalone NFS Server](nfs.md)
  1. [Setup Master Node On-premises](m-node.md)
  1. [Setup Slave Node On-premises](s-node.md)
  1. [Mysql Master/Master Setup](db.md)
  1. [Configure Database Replication](db-rep.md)
