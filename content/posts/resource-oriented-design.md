+++
title = "Resource-Oriented Design"
date = 2024-10-18T14:57:11+03:00
categories = ["Tutorials"]
series = ["Google API Design Guide"]
images = ["https://i.imgur.com/FCe9nLY.png"]
+++

This is the first article in a [series](/series/google-api-design-guide/) in
which I try to digest and summarize the [Google Cloud API design
guide](https://cloud.google.com/apis/design). It is a way to force myself to
read the guide in a more deliberate manner, with the added benefit of sharing
the summaries and notes for anyone who wouldn't necessary want to read the
entire guide.

Here I summarize the first section which serves as an introduction to REST and
resource-oriented API design principles. You will find below my own general
summary followed by individual notes taken from that section.

## Summary and Comments

This is a general introductory section that goes over the origin of the REST
architecture and the popularity of REST APIs, and then it explains the
fundamental concepts of resources and methods as well as their general design
and hierarchy in REST APIs. At the end, there are some examples that
demonstrate resource-oriented design in Google APIs.

The main takeaways are:
- Key terms: resource, collection, and method
- Standard REST methods: `List`, `Get`, `Create`, `Update`, and `Delete`
- A look at resource hierarchy, especially in the provided examples

## Notes

### Introduction to REST

- REST is an architectural pattern that was designed for HTTP/1.1 and for
solving problems related to designing RPC APIs. A REST API is modeled as a
collection of *resources*.

- Resources are the nouns of APIs, while methods are the verbs. In HTTP terms,
resources map to URLs and methods map to HTTP verbs (e.g., `GET`, `POST`, etc.)

- Standard REST methods are:
    + `List`
    + `Get`
    + `Create`
    + `Update`
    + `Delete`

- Custom REST methods/verbs can be created, but for HTTP APIs those methods
don't map to custom HTTP methods. Instead they use the same standard HTTP
methods.

### HTTP/JSON vs. RPC APIs

- HTTP/JSON APIs are the most popular, but for performance reasons (in use
cases such as video content) socket-based RPC APIs are more favorable.

- Both API types are viable options, and both can benefit from the simplicity
of resource-oriented design patterns. 

### Resources and Methods

- Resource-oriented design represents a hierarchy of *resources* (called
"simple resources") and *collections* (called "collection resources"):
    + A *collection* contains resources of the same type.
    + A *resource* contains state and may contain other resources or
    collections.

- A resource hierarchy does not necessarily have a direct one-to-one mapping to
a storage system (e.g., database). REST APIs are more flexible, and a method
related to one resource can affect other resources as well.

- Resource-oriented APIs emphasize resources (data model) over methods
(functionality).

- Favor standard REST methods when they naturally map to certain API
functionality. Otherwise, custom methods may be used.

- The Gmail API as an example of resource-oriented design (read more
[here](https://cloud.google.com/apis/design/resources)):
    + A collection of users: (`users/*`), where each user has:
        - A collection of messages: (`users/*/messages/*`)
        - A collection of threads (`users/*/threads/*`)
        - A profile resource: (`users/*/profile`)
        - ...

