+++
title = 'Reflecting on My Web Development Journey'
date = 2024-07-11T13:54:06+03:00
draft = false
categories = ['Blog']
tags = ['Learning', 'Backend', 'Full-Stack', 'JavaScript', 'Go', 'Elixir', 'AWS']
images = ['/img/codesymbol.png']
+++

There isn't any exact point in time that I could mark as the beginning of the
path to becoming a web developer. I learned programming on R as I was
specializing in biostatistics at the time, and gradually over the course of 6-7
years things went from "orbiting around" web development to making it a direct
part of skill set and a career goal to have.

With that said, I am writing this article in an attempt to recap particular
stages of this journey. This would serve as both a reflection on the past and
some thoughts about the future. I did write similar ideas in earlier articles,
but this one in particular should flesh things out and focus solely on web
development (unlike previous ones that had statistical programming in the mix).

So, without further ado, here goes my story...

## Basic Front-End Development

It shouldn't be surprising that my first skills to build in the web were on the
front-end side of things. The nuance, however, is that I learned front-end
technologies to augment and enhance web-based data reports and interactive
visualizations that came out of some R packages that I used as a statistician.
I used HTML, CSS, and very little jQuery to tweak that stuff, use company
branding like logos and colors, etc. I also learned D3.js and used it in a
[community project](/posts/forest-plot-with-heterogeneity-bands).

Technologically speaking, this is really not impressive at all. In any
[RMarkdown](https://rmarkdown.rstudio.com/) report, the amount of front-end
code I write wouldn't exceed 20-30 lines or something. But I would still be
proud to say that I managed to use these very basic skills to do something that
is considered unique in the field I was working in. It's things like this that
made me discover that business value and technical complexity are not
necessarily highly correlated.

A while later, I joined a team of mostly back-end developers working on
projects that are built with actual web frameworks like Laravel and Django. As
you might expect I handled the UIs that are built with Blade/Django templates.
I was away from the back-end code most (but not all) of the time, but I did
learn a number of concepts. In some cases I even helped the back-end developers
debug some problems.

At this stage, I was at a point where there are lots of concepts that I know
about, probably enough to make it easy for me to start writing full-stack apps
myself and get tangible experience. But at the time, web development was still
at best a side hustle for me, and I only focused on front-end technologies.

## JavaScript

The very logical next step. I started dabbling in modern JS frameworks, mostly
React and Svelte. I added TypeScript in the mix some time later. I was
absolutely blown away by the development experience and tooling associated with
those technologies. Linters, formatters, autocomplete, and all of that happens
automatically in VSCode as you write code or save it. Not to mention that even
basic framework concepts like the component model and reactive state were very
fascinating to me (and still are).

The difference between such workflow and what I was doing before was like night
and day, to a point where I felt a little bit angry at how people would still
write HTML in templating engines with wonky (or even nonexistent!)
auto-formatting or syntax highlighting. Not to mention TypeScript, a language
that give you types, which improve the completion and catches some potential
bugs. How do people not embrace this awesome stuff and keep writing code with
no types or compile-time guarantees like Python or PHP?

Now here comes the funny part: I became a JS fanboy. I was pushing it where
back-end devs were pushing in the opposite direction. Whenever I suggested
doing something on the client, they were reluctant to agree and did their best
to keep it all on the server. I was even starting new projects with full-stack
frameworks like SvelteKit, probably because I was seeking freedom to do more
with the JS code that I write, and also deploy at will on Vercel which made it
easy and fast for me to create and update demos without looking for and
corresponding with someone else to handle that for me.

If you wonder why that last part is funny, it is because I actually am no
longer the JS/TS fanboy that I was anymore. I started experiencing some of the
pains associated with JS. The huge number of Node modules needed for any
framework [feels icky to me](/posts/dependencyphobia). The ecosystem is really
fragmented with all the frameworks, libraries, and runtimes. I feel like the
rug is pulled from under me with updates that, even if backwards-compatible,
would have significant API changes that are considered the standard for the
future.

Overall, I've got a JS burnout, and as of now I'd prefer working with
technologies that are simple and stable. I feel comfortable working with few
dependencies and spending my time diving deeper rather than catching up... So
going forward, I want to write as little JS as I can.

## Tracer Bullets

I've encountered the concept of tracer bullets while reading The Pragmatic
Programmer. In the book, it's a metaphor for a style of development where you
develop a bare-bones feature that covers all the major components or parts of
the stack without necessarily being fully working. This way you can test an
application's architecture, see what works and, even better, you quickly get
proof-of-concept features that are ready for feedback.

While the book uses the concept as style of application development, I think it
does apply to an extent to my current learning goals. So, instead of focusing
on something and trying hard to specialize, I first want to cover as much of
the "full stack" as I can. That way I can get better self-assessment on what I
know, what I don't know, and what specialization I may be excited to dive into
in the future.

### Completing the Full Stack

The first obvious missing piece was back-end development, and the highlight of
this stage in my journey was [Boot.dev](https://www.boot.dev/). I decided to
hop onto Boot.dev for 2 reasons. First, I wanted a bootcamp-style material
which I would take from start to finish and identify what gaps I need to work
on. Second, I was particularly curious about Go, and Boot.dev does teach it. So
that led me on a few months of fun learning and applying this tracer bullet
approach in building simple apps that connect front-end to back-end to
database, applying basic CRUD functionality and the like.

Now comes the next step of building a full-stack application that would not
only apply the concepts that I learned so far but also be packaged as a full
product. This means that I would no longer write the basic CRUD operations and
call it a day. The idea ended up being a [portfolio builder
app](https://github.com/waseem-medhat/skillstackr) and as of the time of
writing this it is still a work-in-progress but very close to an MVP. I want it
to have a good UI/UX, and I need to iron out every little detail that I could
think of. I also want to make it as fully documented and tested as I could. Not
to mention that I intend to deploy it and give it to real users to consume and
potentially benefit from. 

Speaking of deployment...

### Going to the Cloud

There is an additional missing piece that I intend to cover, and that is the
cloud and DevOps part. I don't know how much DevOps knowledge is expected from
back-end developers in the industry, but what I do know is 1) apps are built to
be shipped, and DevOps is how shipping happens, and 2) from a job-search
perspective, AWS and other cloud providers are always listed in the "nice to
have" sections of the developer job requirements. So, learning some of the
services offered by one of those cloud providers will improve my knowledge and
make me more qualified for jobs in a very competitive market. It's an overall
win, I'd say.

Being the most popular and most explicitly mentioned in job requirements, I
picked AWS. I started learning about some of their popular services like S3,
EC2, Lambda, etc. as well as some of the basic networking and security stuff
that works across all these services like VPCs, IAM, etc. Then, I will try
building projects with AWS in mind and see how I can glue these services
together to make an app.

## Building Stuff

As you may gather from the previous sections, the overarching theme in my
current stage of becoming a better web developer is to build stuff. It's not
just writing code or solving isolated problems or coding challenges. I want to
keep building full-fledged products and push them to a state that is as
production-worthy as possible. I want to potentially serve real users and offer
real value.

The first project that I pushed to completion was the [Gopen](/projects/gopen)
CLI which solved a workflow problem that I had, and now I use it on a daily
basis. I also developed many tracer bullet projects like [PMDb](/projects/pmdb)
which is an IMDb-like website, and [MoneyGopher](/projects/moneygopher) to
dabble in the microservices architecture with gRPC. Now I'm mostly working on
the portfolio app but trying to actually perfect the value and UX of this one.

It took me a while to get into this "learning by building" mindset but I'm glad
I did. One reason is to gain more knowledge and experience. I've seen that in
terms of learning and practice, a concrete, serviceable product is more than
the sum of its parts. Some concepts or best practices don't work well with each
other, and you couldn't know that until you put them together yourself. Some
feel promising theoretically but their appeal might become lackluster in
practice or during maintenance. It's things like that are only understood with
real-world experience instead of learning individual concepts in isolation.

Since I'm seeking work as a developer, it won't be a surprise that I'm also
developing fully working products for portfolio purposes. Just like AWS, many
things related to full-stack development (e.g., product "packaging," covering
most or all edge cases, deploying the app to production, etc.) would fall under
the "nice to have" category. But again, I would take them seriously in order to
demonstrate my knowledge even if they aren't strictly required. I hope that my
portfolio doesn't just communicate my abilities to write software but rather my
abilities to write *high-quality* software.

## Experimentation

I couldn't paint a full picture about my past and future as a web dev with the
previous sections alone. I don't just want to "get good" and find a job, but I
also want to have fun and try new things in the process. It was curiosity that
got me to write code in the first place. So, I'm trying my best to find the
sweet spot between having fun trying new things and excessive tech-hopping that
might do more harm than good.

I've been mostly writing Go for my past projects and courses, but I did learn
Clojure before and played with it for two months. As a functional programming
enthusiast, I recently got a desire to try a new functional language, but at
the same time I wanted to keep things practical as I want to build full-stack
apps. I felt Elixir is a good choice for me in the current situation, and the
primary reason for this is definitely Phoenix. I don't think any functional
language has a fully featured web framework like Elixir has Phoenix.

So, I'm using Phoenix to make the portfolio builder, and it's a fun experience.
I will also probably use Elixir to write another project that better leverages
the concurrency features. Concurrency is a relatively new topic for me that I
want to dive deeper into. If I got an itch to try another language, it will
probably be either OCaml or Haskell. We'll see.

## Final Notes

So that was my ramble. Probably my longest article yet. But I am glad that I
was able to contemplate and clarify my progression in web development, even
though the are probably some missing details here and there. I feel really
lucky and privileged to discover and enjoy development as a hobby, a craft, and
a career.

Thank you for reading!
