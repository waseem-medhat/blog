+++
title = 'IAM Shenanigans'
date = 2024-09-25T14:57:07+03:00
draft = false
categories = ['Blog']
series = ["I Guess I'm Doing Cloud Now"]
images = ["https://i.imgur.com/GhhmuYt.png"]
+++

After [moving my blog to AWS](/projects/moving-my-blog-to-aws), the next step
for me was to try interacting with S3 programmatically. I am currently building
a [portfolio builder app](https://github.com/waseem-medhat/skillstackr) in
Elixir, and like so many other web apps out there, it involves storage of
static files uploaded by the user. So, I used this as another opportunity to
get in more contact with S3 as one of the most common AWS services, but more
importantly, I got more familiar with IAM concepts and best practices.

So, this article describes the IAM setup I had for this goal. Keep in mind that
this setup was done for development purposes on my local machine, which means I
had freedom to explore without worrying about loose permissions at first. It
also means that the final setup would be slightly different in production when
I deploy the app on an EC2 instance.

## Initial Implementation

I always like to start small and rough with only one goal: *make it work*. So,
I created a bucket, wrote some back-end logic to interact with it, then I
configured the client SDK (`ExAws`) to authenticate using my own access keys.
It worked fine and was very straightforward to set up. However, there are
multiple problems with this approach:

- Since the application uses the access keys that I created for my own IAM
user, that gives it `AdministratorAccess` permissions which means it can
practically do anything on AWS. This is clearly not good at all from a security
perspective and a direct violation of the principle of least privilege
encouraged by AWS.

- From an organizational and best-practice perspective, it doesn't make much
sense for an application to authenticate with a user's credentials. IAM roles
would be the more appropriate identity to assume in this case.

But overall this was a successful attempt at making it work. Next step is to
*make it right*.

## Current Implementation

There are multiple things that needed to be done in order to restrict the
permissions and follow best practices. This diagram explains the current state
of authentication/authorization flow between my app and the S3 bucket after all
changes have been made.

![IAM Flow](https://i.imgur.com/v71rZqF.png)

The details, starting from the S3 bucket, are as follows:

- The **S3 bucket policy** had to be restricted so that it can only allow get,
put, and delete object operations by a certain IAM role.

- The **IAM role** has a permissions policy that allows it to get, put, or
delete objects in the bucket. It also includes a trust relationship that
specifies which identities can assume the role. In my case, the current target
identity is an IAM Identity Center user.

- The **Identity Center user** is one that I created as part of an AWS
Organization. It is separate from my administrator user and is associated with
a permission set that only allows it to assume the role that I set up.

- The **AWS CLI** on my local machine is configured so that it can authenticate
via the Identity Center user and let it assume the role. The configuration
includes a profile for the role which references another profile for the user.

- Finally, the **back-end app** is configured so that the SDK uses the role's
CLI profile and assume that role when interacting with AWS services.

As someone getting started with AWS, it wasn't a straightforward task to grasp
all these concepts enough to arrange them in my head and in a diagram like the
one above, much less applying them. Luckily, with enough time of reading the
documentation, AI prompting, asking around for help, and letting it all
marinate in my head, I was able to put the pieces together.

## Lessons Learned

Despite the end goal simple being object handling in an S3 bucket, the bulk of
what I learned in this endeavor has been IAM, and that is why it has been the
focus of this article. I got a better understanding of concepts like roles,
policies, Identity Center, organizations, and applying least-principle
permissions. Also, the recurring theme of my AWS learning (apart from drawing
diagrams) is how fascinating it is that platform-as-a-service companies managed
to wrap all of this under a couple of button clicks.

Overall, I believe this has been one of the essential parts to learn in AWS
because surely no resources can be accessed without the correct permissions in
place. So, I will be looking forward to applying this in future projects.
