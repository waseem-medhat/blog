+++
title = 'What Is Cloud Computing, Really?'
date = 2024-11-24T18:39:34+02:00
draft = false
categories = ["Tutorials"]
tags = ["Cloud", "AWS"]
images = ["https://i.imgur.com/0iESPcD.png"]
+++

The cloud has become a pretty familiar term in this day and age. However, there
is a precise definition and a set of criteria that formally define what cloud
computing really is. So, in this article I briefly go over these criteria,
which I believe are important to know for people working with the cloud or
studying to get certified. They may also be interesting to know for other
people as well.

The content in this article is directly based on the [NIST definition of cloud
computing](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-145.pdf),
although the document includes other topics like service models and deployment
models. Also, I mention some examples to clarify the concepts, and these are
based on AWS since this is what I know, but the concepts still apply to any
cloud provider.

## Essential Characteristics of Cloud Computing

There are five criteria that must apply to a service in order to be considered
cloud computing. In the subsections below you will see each one of them with a
direct quote from the NIST document followed by my attempt to simplify it.

### 1. On-Demand Self-Service

> A consumer can unilaterally provision computing capabilities, such as server
> time and network storage, as needed automatically without requiring human
> interaction with each service provider.

Let's break this down into two parts:

- The "on-demand" part is apparent from the fact that we can launch most
resources on AWS like EC2 instances, Lambda functions, S3 buckets, etc. right
away and as many times as possible. We provision resources *on demand*.

- The "self-service" part is about being able to launch those resources without
the need for submitting requests or any form of human interaction. As long as
you have access to the AWS APIs through the UI console or the CLI, you're good
to go.

### 2. Broad Network Access

> Capabilities are available over the network and accessed through standard
> mechanisms that promote use by heterogeneous thin or thick client platforms
> (e.g., mobile phones, tablets, laptops, and workstations)

This one simply means that cloud services like AWS are accessible by any device
that is connected to the internet. Both this point and being on-demand
self-service make it a trivial task to spin up cloud infrastructure.

### 3. Resource Pooling

> The provider’s computing resources are pooled to serve multiple consumers
> using a multi-tenant model, with different physical and virtual resources
> dynamically assigned and reassigned according to consumer demand. There is a
> sense of location independence in that the customer generally has no control
> or knowledge over the exact location of the provided resources but may be
> able to specify location at a higher level of abstraction (e.g., country,
> state, or datacenter). Examples of resources include storage, processing,
> memory, and network bandwidth.

This can also be broken into two parts:

- Resource pooling and multi-tenancy mean that AWS manages infrastructure that
is used by multiple customers. In other words, multiple customers can have
isolated AWS resources that (under the hood) share the same underlying physical
infrastructure. However, they are logically isolated as far as the customer is
concerned.

- Location independence in the case of AWS means that when we as customers
launch AWS resources, we don't know exactly which server or data center
contains these deployed resources. However, we interact with AWS at more
abstract levels like regions and availability zones (AZs).

To put this in an oversimplified example, AWS has data centers all over the
world that contain servers with huge amounts of storage and compute power. On
each one of those servers is a way of creating smaller virtual machines (VMs).
When you launch an EC2 instance, you're creating one such VM that runs on one
of those servers. You can specify the region and AZ in which this VM resides
(e.g., us-east-1a), but that does not inform you exactly which data center has
your VM. The lowest level you can manage as a customer is the AZ level.

### 4. Rapid Elasticity

> Capabilities can be elastically provisioned and released, in some cases
> automatically, to scale rapidly outward and inward commensurate with demand.
> To the consumer, the capabilities available for provisioning often appear to
> be unlimited and can be appropriated in any quantity at any time

Elasticity here refers to scaling out (adding resources) and in (removing
resources) according to the current demand. A prime example of this is EC2 and
auto scaling groups, which can be configured to add or remove EC2 instances
based on usage. The ability to scale out means that we can ensure higher
availability for our applications, and the ability to scale in means that we
don't have unnecessary resources running.

### 5. Measured Service

> Cloud systems automatically control and optimize resource use by leveraging a
> metering capability at some level of abstraction appropriate to the type of
> service (e.g., storage, processing, bandwidth, and active user accounts).
> Resource usage can be monitored, controlled, and reported, providing
> transparency for both the provider and consumer of the utilized service.

The main idea of this point is that all forms of resource usage are measured
from both billing and monitoring perspectives. Most cloud resources follow a
pay-as-you-go pricing model. Together with elasticity, this eliminates the need
for over-provisioning and makes costs reflect actual usage. The monitoring and
reporting capabilities also are useful for logging, analytics, regulatory
compliance, audit trails, etc.

## Conclusion

To recap, for a service to be considered cloud computing it has to satisfy the
five criteria explained above: on-demand self-service, broad network access,
resource pooling, rapid elasticity, and measured service. I hope that with this
brief article you learned something new or refreshed what you already know
about the what cloud computing really is.

Thank you for reading!

* * *

- Cover photo credits:
https://www.vecteezy.com/free-vector/cloud-computing-background
- Service models diagram credits:
https://dachou.github.io/2018/09/28/cloud-service-models.html
