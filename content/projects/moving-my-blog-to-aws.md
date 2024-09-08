+++
title = 'Moving My Blog to AWS'
date = 2024-09-08T18:11:42+03:00
draft = false
categories = ['Blog', 'Projects']
tags = ['AWS']
series = ["I Guess I'm Doing Cloud Now"]
images = ['https://i.imgur.com/VOXpQCi.png']
+++

My first (real) cloud project was to use AWS S3 for static site hosting with a
custom domain, where previously I had it on Netlify with the default
`.netlify.app` domain. It is a relatively simple project, but since this is my
first foray into working with the cloud, there was some experience to gain and
some nuances to account for after the simple act of putting static files in a
bucket.

I chose the fabled DNS haiku as the thumbnail for the article because I did
have my first "DNS moments" with this project. And without further ado, I'll
briefly share some notes about the project.

## Architecture

The following describes the general architecture of the blog. Of course there
were other small bits of configuration here and there to make everything work
together but I will mostly be mentioning the high-level stuff:

![Blog architecture](https://i.imgur.com/o84bU2c.png)

- The blog content is hosted on a static hosting-enabled S3 bucket.
- Since S3 doesn't support HTTPS directly, two things needed to be done:
    + Got an SSL certificate from Amazon Certificate Manager (ACM)
    + Set up a CloudFront distribution for the bucket with the SSL certificate
- To use my custom domain, I added CNAME records in my DNS to allow for both
the root domain (`overthinking-development.blog`) and the
`www.overthinking-development.blog` subdomain to point to the created
CloudFront distribution.

Overall, nothing was groundbreaking or challenging once I understood the how
these services and DNS all worked. I did have multiple fights with the DNS,
though, especially when I was adding CNAME records for the purpose of
validating my SSL certifcate. After some searching in the official
documentation and some StackOverflow posts, I solved the problem I had and
learned something new about DNS.

One quality-of-life improvement I did was to set up the AWS CLI on my local
machine in order to update the content with the `aws s3 sync` command without
having to log into the console and point-and-click my way through.

## Next Steps

There is not much else to do in a project like this. But one thing I'm thinking
about is to do a redirect from the `www` subdomain to the root domain instead
of setting them both in the DNS. As far as I know the only visible change this
will cause is that URLs in the browser will be consistent, since the final
result will always be `overthinking-development.blog`. It will also serve as
some learning and experimentation with CloudFront functions, which I am going
to use for this purpose.

Also, although I set up the AWS CLI to update the content with a single
command, a fully automated approach might be done by setting a CD pipeline. I
did not research the matter yet, but I would guess it could be done by setting
up a GitHub action with the AWS CLI and the proper configuration and
credentials.

## Final Notes

Despite its simplicity, this project (at the time of writing this) was the most
complicated thing I've done on the cloud. Previously, I only used services like
Netlify or Render where the deployment process is simply linking a GitHub repo
and clicking a couple of buttons. AWS work, on the other hand, is at a much
lower level which shifted some complexity to me. Not to mention that it was my
first time to buy a domain and play with DNS records.

Overall, it was an exciting experience. Learning new things and solving
problems in tech is always fun, and if anything, it got me excited to do more
with AWS. Also, interestingly, I feel that working with AWS is giving me a
different level of appreciation for what some services provide to make the
experience of putting software in the cloud much smoother, from 2nd-tier cloud
providers like Linode and DigitalOcean to the more hands-off services like
Netlify, Vercel, Render, etc.
