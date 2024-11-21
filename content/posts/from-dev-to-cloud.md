+++
title = 'From Dev to Cloud'
date = 2024-11-14T13:17:27+02:00
categories = ['Blog']
series = ["I Guess I'm Doing Cloud Now"]
images = ["https://i.imgur.com/gROB3vB.png"]
+++

I started this ["I Guess I'm Doing Cloud
Now"](/series/i-guess-im-doing-cloud-now/) series  more than two months ago to
document and share what I'm learning as someone new to the cloud in general and
AWS in particular. So far, the cycle has been: get introduced to a new service,
try to work with it, reflect a little on how it may be useful, repeat.

This article, however, is a chance for me to take a step back and consider what
I learned so far from a big-picture perspective after getting some knowledge
and hands-on experience.

## Background

I got into tech primarily because I enjoyed writing code and solving problems,
and for the longest time I did just that while ignoring the cloud and DevOps
side of things. Even whenever I wanted to deploy a front-end or a full-stack
application, I went for the most abstract, hands-off types of services like
Vercel or Render. The "anti-cloud" arguments and related horror stories that
circle around the internet didn't help with triggering my interest either.

However, I did eventually take the plunge to learn AWS because:

- I don't like not knowing something in tech. Even if I end up learning very
little in the grand scheme of AWS, it would still be beneficial for either
working with DevOps engineers or developing my own projects.
- Even developers are now expected to have cloud skills, and I don't see why I
would consciously give up on an advantage in the job market.
- It could be an actual career path to pursue in and of itself, because why
not?

This should set the stage for the rest of the article.

## Initial Bump

Trying a new library, framework, or even a programming languages became a
relatively easy task to do. There is a baseline of concepts that are
transferable between different development technologies with mostly
surface-level things to learn (e.g., syntax). The cloud, however, was a
different beast entirely. There is relatively little technical knowledge that I
already had and could take into AWS to make my life easier. To be fair, some
bits of knowledge helped, including YAML, JSON, high-level HTTP, Linux, and
other things. But none of this would make it easy to understand the sheer
number of concepts and services in AWS.

For example, I understand that I can connect to an EC2 instance via SSH and
navigate there easily since I know a thing or two about Bash and the Linux
filesystem. But before I could even connect to an instance, there were many
concepts I had to learn other stuff needed for working with EC2 such as like
VPC and IAM. This is just one of many cases in which I found out that there was
a lot to learn especially in terms of networking and security, some
AWS-specific and some more general like the OSI model, DNS, etc.

However, once I got past the initial bump, things are becoming a little bit
smoother (I think), especially after forming some understanding about essential
terminology and concepts that form the common denominator for most services.
Let's hope things remain that way.

## Less Coding, Same Problem Solving

It is almost obvious, but working with the cloud involves way less code than
development. Even when you factor in IaC, it counts as "configuration" more
than "building" in my book. The difference may be a bit hard to pin down
exactly, but I still think that writing YAML or JSON files to be handed to AWS
to spin up resources barely counts as programming. So, since these days I am
primarily focusing on getting some cloud skills under my belt, I miss writing
code more often.

With that said, though, problem solving is something that *does* exist in the
cloud that I also love in development. The process of figuring out the ideal
architecture for a certain application or service as an attempt to solve a
problem, that's something that I find quite exciting. One example of that was
[this video about securing the Slack API with AWS
CloudFront](https://www.youtube.com/watch?v=oVaTiRl9-v0). Without sidetracking
into the talk's details, it demonstrates adding a service to a stack which
increases security with some performance improvements on top.

One thing that I knew already as a developer was CI/CD. Ever since I discovered
it, I found it quite fascinating how you can automate most of the work that
goes into linting, running tests, staging/production deployments, etc. while
protecting the main code branch. Good CI/CD pipelines make the whole process of
updating and deploying code feel like a well-oiled machine. So, this made me
grow some appreciation for DevOps.

## (Possibly) Less Chaos

This may or may not be true, or it may be true for me given my own past
experiences, but I'm getting the feeling that learning and working in the cloud
is potentially less chaotic than development. To be clear, I know that in a
real world setting, things do get messy for both developers and DevOps
engineers. That's just the nature of software and infrastructure that serve
real users, undergo business requirement changes, etc. In other words, I am not
talking chaos in *projects* but rather more generally in *ecosystems*.

For instance, AWS and other cloud providers offer certificates, and that gives
you some defined structure to the content you want to learn and how to get
qualified (regardless of whether or not you intend to take the actual exams).
On the other hand, I found that the idea of being "qualified" in software
development means different things to different people. To some it's experience
with a language/framework, to others it's understanding how the CPU and memory
work, to others is having solid conceptual foundation, etc.

As for the AWS documentation, my experience is positive so far, and things
there usually clear enough for any given service I read about. With
development, the documentation quality for any language or library is variable
and very much dependent on how much effort the author is willing to put into
it. That doesn't automatically make things smoother in AWS (sometimes the
services themselves are just complicated), but at least I know I have a single
source of truth that I can always refer to and read more. I don't like it when
I rely too much on Google, AI, and Medium articles because the official
documentation is inferior.

I absolutely love programming and open source software, but it can often be a
wild west. Maybe that's part of its beauty, but that doesn't make it less
chaotic. Or maybe this is just classic "grass is always greener." Only time
will tell.

## Final Notes

Am I a cloud convert now? Not entirely, but I definitely have grown some
(unexpected) appreciation for the cloud. It might be too much overhead for solo
developers trying to just deploy a monolithic application and get on with their
lives. Personally, I wouldn't enjoy developing a web app *and* managing its
infra with AWS at the same time. However, as a speciality on its own, cloud
architecture is quite interesting, and I look forward to learning more of it
and rambling even more in this blog.

Thank you for reading!
