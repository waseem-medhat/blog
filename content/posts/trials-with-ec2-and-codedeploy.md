+++
title = 'Trials with EC2 and CodeDeploy'
date = 2024-10-23T12:20:46+03:00
draft = false
categories = ['Blog']
tags = ['AWS']
series = ["I Guess I'm Doing Cloud Now"]
+++

In this article I document my first interactions making an initial deployment
for [a project of mine](https://github.com/waseem-medhat/skillstackr) on an EC2
instance and setting up continuous deployment with CodeDeploy.

## Services Overview

This is a relatively simple workflow that will involve two AWS services in
addition to GitHub.

- **EC2**: the very popular AWS compute service. I should have a single
instance (VPS) to host the application's production artifact plus the
CodeDeploy agent.
- **CodeDeploy**: the service used for continuous deployment.
- **GitHub Action**: used for running the build process for the application and preparing the compiled artifact to be deployed on the EC2 instance.

## Launching an Instance

The first step was to launch an EC2 instance. Before doing that, I started to
educate myself a little bit about virtual private clouds (VPCs) using this
[great tutorial by 'Be A Better Dev'](https://youtu.be/3FumWkHSusY) just to
understand what the wizard does for me in terms of the networking parts around
the instance. Afterwards, launching the instance was very straightforward.

The only customization I made in that step was to use a custom name for the
security group created by the wizard to be more descriptive than the default
`launch-wizard-1`. Also, I created a key pair and set up the security group to
allow inbound SSH traffic so that I can connect to it from my local machine.
Finally, I installed the CodeDeploy agent.

## 
