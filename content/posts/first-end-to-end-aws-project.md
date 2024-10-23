+++
title = 'First End-to-End AWS Project'
date = 2024-10-23
draft = false
categories = ['Blog']
series = ["I Guess I'm Doing Cloud Now"]
images = ["https://i.imgur.com/lI2kb4O.png"]
+++

I'd like to share a couple of ideas based on this project that I built by
following a [video by 'Tiny Technical Tutorials'](https://youtu.be/K6v6t5z6AsU)
which is my first exposure to an AWS-centered project that uses more than just
a couple of services to architect a full-stack application. I thought this
would be worth a recap because, aside from learning a new thing or two about
some services, it triggered some thoughts that will probably affect my future
learning and interactions with AWS.

The next section summarizes the project to give you some context, and following one has my own comments and thoughts.

## Architecture Overview

Generally speaking, here are the individual pieces involved in this app (the
architecture of which is displayed in the cover photo):

### Application Code

- A front-end app built by vanilla HTML, CSS, and JavaScript and configured to
work with Cognito and API Gateway.
- The source code is hosted on a GitHub repository.

### Amplify

- I call it AWS's attempt at making a hands-off platform-as-a-service like
Netlify. It may or may not be more than that, but at least it was used this way
in this project's scope.
- It was configured to deploy from the project's GitHub repo and re-deploy
automatically after any new commits.

### Cognito

- That's the service responsible for holding the "user pool" and handling the
authentication functionality (password policy, sending emails with verification
codes, etc.).

### API Gateway

- It acts like a REST API with an endpoint that receives HTTP requests, runs
the specified Lambda function, and returns the response (not to indicate that
API Gateway can *only* be used for that).
- Since the tutorial built the project using the UI console, this step in
particular felt like a "ClickOps" way of building a RESTful backend (more on
that later).

### Lambda

- A single serverless function was written to execute some back-end logic that
involves writing to a DynamoDB table.

### DynamoDB

- This is a key-value NoSQL database.
- Only a single table is used in this app, which the Lambda function writes to.

## My Thoughts

Like I said, this has been my first exposure to a full-stack application whose
architecture is built end-to-end with AWS services. Compared to my previous
interactions with the cloud, this one triggers two main ideas.

### Replacing the Monolith with AWS Services

I was coming into AWS looking forward to this in particular, which is how
individual parts of the back-end functionality of an application can be split
and handed to a separate AWS service. Here is how I feel that happened in this
project by attempting to make a mapping between parts of a typical back-end
functionality in a monolith and the AWS services that "replace" them in this
project.

| Monolith | AWS |
|-|-|
| File server for the front-end app | Amplify |
| Routing | API Gateway  |
| Handler functions/controllers | Lambda functions  |
| Auth/JWTs | Cognito  |
| "Users table" in a database | User pool in Cognito |
| Logging | CloudWatch |

Of course, just like back-end development frameworks and design patterns, there
is usually more than one way to architect an app on AWS, especially with the
huge number of services (and features per service) that are available. So, the
more I learn and understand, the more flexibility I'll gain when it comes to
setting an app's architecture.

### The Need for Infrastructure-as-Code 

Racking up more services for an application gets unwieldy pretty quickly, and
that application isn't even that complicated, not by a long shot. What makes
things worse is that (to my knowledge) I see no apparent notion of an
"application" that groups individual services: an app's DynamoDB table would be
one among multiple unrelated ones in the DynamoDB console dashboard, and the
same goes for Lambda functions, IAM roles, or any other resource.

So, this project ended up being a huge motivation for me to learn IaC (probably
Terraform) and use it for my future projects. It should serve as a sort of
central documentation/config for all resources that are needed to run a certain
application, not to mention the obvious benefit of automating all the pointing
and clicking in the console. It is something extra to learn and get used to for
sure, but I feel that the ROI is worth it at this point.

## Final Notes

Not much effort went into this project because I was following a step-by-step
tutorial. However, it was a bit of an eye-opener when it comes to grokking AWS
as a platform for building full-stack applications. That doesn't mean I now
truly grok AWS, but it definitely felt like a step in the right direction after
seeing AWS services that cover the whole stack and developing a first-hand
understanding of how IaC can be beneficial.

Thank you for reading!

* * *

Cover image is taken from the same tutorial.
