+++
title = 'MoneyGopher'
date = 2024-05-08T15:47:27+03:00
categories = ['Projects']
tags = ['Go', 'Docker', 'Microservices', 'Backend']
images = ['https://i.imgur.com/7QgDQ42.png']
+++

[Check the project's GitHub repo](https://github.com/waseem-medhat/moneygopher)
for the source code, and any relevant documentation. At the time of writing
this the features are still work-in-progress, but I was able to lay down the
architecture and spin up service containers and have them talk to each other
(and to the client via the gateway) plus some automation tooling.

## Description

Microservices is one of the architectural patterns that help with scalability
of web applications. It is implemented by separating an application or system
into independent "services" that communicate with each other via the network.
With that in mind, it also has organizational benefits since each service can
be owned and maintained by a separate team in the company.

I wanted to try to implement that pattern and get first-hand experience while
discovering its advantages and disadvantages. I especially wanted to focus on
things that are specific to microservices like spinning up multiple containers
or tooling/code generation. So, MoneyGopher was my way of doing exactly that.

## Technologies

The stack is built around Go, gRPC, and protocol buffers (protobufs). There is
also lots of tooling to help automate the development process or the code
generation for new services.

### Architectural Design

This diagram shows a simplified representation of the architecture. I'll
explain the architecture in some detail in the following subsections.

![design](https://i.imgur.com/yPc1n68.png)

### API Gateway

The API gateway is service responsible for receiving requests from (and
returning responses to) a front-end application. In this way, it acts like a
REST API which communicates with the front-end via JSON. Depending on the
request, it communicates with the internal gRPC services to retrieve data or
execute any logic, which makes it also a gRPC client in that sense.

### gRPC Services

Each service in the application is concerned with an isolated part like
transactions, OTPs, etc. Each service is its own gRPC server and has its own
database. The only exception is the OTP service, which doesn't have a database
because it stores OTPs in an in-memory cache since OTPs are not meant to be
persistent.

### Docker

For the API gateway and the gRPC servers, each service is spun up in its own
Docker container. This should mimic a scenario in which each service is
deployed independently. I used Docker's network feature to provide a "virtual"
network through which all the services can communicate with each other.
I also used Docker Compose to be able to easily spin up all these containers,
set up the network, and add environment variables needed by the services.

### Tooling

Since the project has a relatively large number of moving parts, I felt a need
for writing some tooling to automate some parts of the development process that
would be really tedious otherwise. These parts include executing database
migrations, generating gRPC (Go) code from Protobuf files, compilation of the
Go binaries, building the Docker images, and spinning up the containers from
the Docker Compose file.

I also experimented with developing a code generation package to spin up new
services if I need them. At the time of writing this I built a minimal package
that relies on Go's templating system to create new files and update their
contents depending on the provided name of the new service. It still needs some
work (or possibly an alternative approach), but for now it still saves me some
time and effort.

## Skills

- Microservices
- Docker (& Docker Compose)
- gRPC
- Protocol buffers
- SQL
- GNU Make
- Bash scripting
