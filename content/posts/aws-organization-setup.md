+++
title = 'AWS Organization Setup'
date = 2024-11-23T16:37:40+02:00
categories = ['Blog']
series = ["I Guess I'm Doing Cloud Now"]
images = ["https://i.imgur.com/8rsCLV2.png"]
+++

In this article, I go briefly over AWS Organizations, what they are used for,
as well a setup that I did with my own acount and will experiment with in the
future.

## Core Concepts

This diagram (from the [official AWS
docs](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html))
is an overview of AWS Organizations and related concepts, which I try my best
to explain below.

![AWS organization structure](https://docs.aws.amazon.com/images/organizations/latest/userguide/images/AccountOuDiagram.png)

The general idea of AWS Organization is that it is a service that helps with
the management of multiple accounts.

- From my perspective as a solo developer, they are a nice way to logically
group the resources that I create on AWS. Otherwise, I would have one account
on which I deploy everything, which could make things a little hard to manage
and keep track of.
- From a larger organization perspective, Organizations could be even more
valuable where it can be used to manage multiple accounts, define a hierarchy
that matches the company structure, control access to resources, consolidate
billing, and more.

With this in mind, the next summarizes some of the core terminology and
concepts of AWS Organizations:

- An **organization** is created by a standard AWS account. Once it is created,
that account becomes the management account for that organization.
- The **management account** is "the ultimate owner of the organization" as the
documentation states. It can create/invite other accounts and attach policies
to accounts/OUs.
- **Member accounts** are any accounts in the organization other than the
management account. They can be created by the management account. Also,
standard accounts can be invited to become member account of an organization.
- **Organizational units (OUs)** are simply ways to group accounts in an
organization, and they can be nested to form a hierarchy.
- The **organization root** is simply the top level of the organization
hierarchy. So, when you create an organization at first you start with the root
and the management account.
