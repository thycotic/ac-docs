[title]: # (Architecture Description)
[tags]: # (thycotic access control)
[priority]: # (201)
# Architecture Description

The goals of this topic is to describe

1. the topology of Thycotic's infrastructure that

   * supports high availability 
   * can scale according to the incoming traffic
1. the monitoring of the applications


## Breaking Down the Services

Access Control collection of micro-services that interact together. Some are deployed on isolated hosts and some are clustered together. There are four (4) clusters of services:

1. the panel services that consist of

   * the admin dashboard 
   * the API
   * LDIFizer
1. the proxy services that consist of 

   * the SSH piper proxy
   * the RDP proxy 
1. the router service
1. the Vault’s [1] secrets management service

Each service is independently configured, deployed and managed. However, services that belong to the same cluster are deployed to the same hosts, thus must scale together.

## Topology

In this section, we will describe components that are used to host each cluster of services and how they are interconnected.

All the various components are deployed within a Virtual Private Zone (VPZ).

### Panel Services

This is the most complex cluster of services in Thycotic's access control solution. __Figure 1__ shows an overview of its topology.
Load Balancer (LB) The internet-facing component. The main role of the LB is to automatically distribute incoming traffic to instances that host the panel services. Additionally, (optionally) it handles the HTTPS encryption & decryption process (SSL termination).

The services running on those instances are thus protected from failures in a single location. There will always be at least one host available to handle requests. Unhealthy hosts are automatically detected and bypassed so that the services are getting the computing capacity we want.

The panel services require access to MySQL databases. Thycotic uses a relational database service that supports the MySQL engine and can be used as an external re-source.

The admin dashboard regularly defers the processing of time consuming tasks by submitting them to a queue. An idle worker can then accept the task and process it. Even distribution of labour across all workers requires all the hosts to connect to the same queue. We achieved it by using Redis. It is a scalable, fully managed message queuing service that works out of the box with our application framework.

Caching is enabled on the Admin Dashboard’s php framework. In order for the cache to be consistent for all the cluster.

The SSH piper service can store session log files in object storage that are later accessed by the Admin Dashboard. The admin dashboard has read-only access to the files, so the admin cannot modify the logs in any way.

## Monitoring

A lot of thought has been put into the monitoring plan of the infrastructure and application components of the Thycotic Access Control solution. The definite goal is to identify and easily debug any single or multi-point failures. __Figure 3__ shows an overview of the monitoring scheme. All the application logs are kept centrally.
