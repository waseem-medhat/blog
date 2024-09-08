+++
title = 'Podcast: Building Better CLI Tools with ThePrimeagen'
date = 2023-11-11T22:11:04+02:00
draft = false
tags = ['Backend', 'JavaScript', 'Go']
categories = ['Blog']
series = ['Content Reviews']
images = ['https://i.imgur.com/lrMggUi.png']
+++

Backend Banter has been one of my favorite podcasts lately, and ThePrimeagen has been one of my favorite YouTubers lately. So, what's a better way to start a series of content reviews than reviewing the [*Backend Banter episode with ThePrimeagen*](https://www.youtube.com/watch?v=ae1PM_jpNoA)?

No further introduction is needed. Let's go!

## Refactoring

Prime mentioned that he wrote code for a game that produced a stack overflow, and that got him to refactor the code to fix that problem. That led them to talk about refactoring and breaking down code into logical pieces.

This part is hugely interesting for me. Especially when they said that the entry point (or top-level) part of the code should be declarative. I find doing that makes me happy with my code from a stylistic or organizational aspect. But then Prime said that it makes the program easier to extend, which I never got to think about given my limited experience.

At the time of writing this, the only personal project I grew to completion was [Gopen](https://github.com/waseem-medhat/gopen), a CLI that quick-starts coding projects by configuring a default editor and some directory aliases. I started coding everything in one file and then kept refactoring as the code grew until I reached a somewhat organized structure similar to what's described above with a "main" entry point that has a `switch` statement that checks what sub-command is given and runs a "handler function" accordingly. That entry point is the most simple and declarative part of my project

## Inheritance and Footguns

I have nothing to say about inheritance, or OOP in general, other than I never got interested in it, and it never made sense to me. Not in the sense that *I didn't understand it*, but rather that I didn't understand *the purpose* of it. A huge chunk of typical software engineering tasks can be done directly using data structures provided by the language without really having to make abstractions on top of abstractions with getters and setters and whatnot... I don't know. Just my thoughts. I'd rather either use a simple approach in my development (like what I'm seeing so far in Go) or go all-in with functional programming in a language like Clojure or Haskell.

That discussion about inheritance tied into talking about footguns and what counts as a "bad mistake," and I like what they said here: Instead of parroting what other people say about something being good or bad, it's always better to try that thing yourself and decide given your perspective and critical thinking.

## Mocking

When I listened to the podcast, I knew nothing about what mocking meant, but they explained it well. Their point was to make functions that can be testable without mocks because the presence of mocks means that the function does more than one thing and should be split into multiple functions. I wholeheartedly agree with that with nothing special to add.

## Maturity and Discipline

At that part of the podcast, Prime and Lane talked more about Prime's backstory. Turns out that the "cliche" of hard work, discipline, and cutting off bad stuff from your life actually works. It got Prime through bad phases in his life, and that's quite commendable.

Let me go on a little rant here... I see a lot of people who get into a victim's mentality, blaming all the bad stuff around them and how life is so hard, thinking that they *can't* do something because life won't let them. They might also call out successful people for being lucky or having a headstart. I had some feelings like this for a while, but not anymore. While some people do get lucky, I strongly believe that everyone can make it where they want with enough work and self-discipline.

## Hot Take: PHP &gt; React

Prime said that he'd built a startup using a PHP app. Then, he went on to say that he wouldn't have been able to build it with React because older tech was easier. He and Lane got to expand more on the topic of why tech is getting harder, which mostly boils down to having a larger mental model and more moving parts to deal with - versus getting a VPS and deploying a simple PHP app with a database.

This is exactly what got me to flee from the front-end ecosystem. It is now full of complicated JavaScript frameworks, and all of them are about rendering UI... except that front-end frameworks are now leaking into the server side. While back-end development still has its own shenanigans, it's still a much simpler and more stable environment to learn and grow in than JS (that's at least the way I see it). I'm really happy doing Go for the time being, and it's the only language I got to actual project completion with. For me, that's something.

## Building CLI Tools

This is not only the topic of episode's title but also where a lot of goodies have come out from both Lane and Prime. Also, this is gonna be the bulk of the article, so I'll split it into subsections.

### CLIs as Portfolio Projects

First, Lane said that CLI tools are great portfolio projects for backend devs because they are much more interesting than a typical, random REST API. Also, CLIs are more likely to get picked up by other devs on GitHub. This exactly happened to me with [Gopen](https://github.com/waseem-medhat/gopen). I didn't imagine this would happen, but one fellow Go dev liked it and started improving it.

### Solving Develoeprs' Problems

Prime then said that he likes building for developers because they (or we) are different from customers. So, he knows well what a developer's problem is, and developers can better explain issues in his solution. He also says that he likes generally making things better, solving problems, etc. I would argue that the problem-solving mindset works for both building for developers and customers. It's just that they're entirely different sets of problems, and the developer's problems are more understandable and relatable for us.

I've been mostly in the building-for-customers camp. My last couple of years have been a mix of biostatistics and some frontend development, which is all technical, and I was always directly dealing with business teams, (non-technical) management, and customers. It was a non-trivial challenge trying to understand what the business or the customer wants because there is always a huge gap between their high-level, very rough objective and the implementation details.

### Unix Philosophy

The Unix philosophy consists of multiple principles, but I believe when most people refer to it they usually mean the part about "doing one thing well." Essentially, it's the principle of developing small programs that have a single responsibility instead of a big one with multiple features.

Prime says he's a fan of the Unix philosophy for the most part, and so am I. I wouldn't be exactly sure if this can apply completely to today's web app development, but I think this single-responsibility principle still very much applies to CLI tools or even modules or independent parts of a single code project.

### Dogfooding

Lane mentions that he likes building for developers because you can "dogfood your own thing." This means that you would write a tool to solve a problem you have yourself. Again, I did this with Gopen, and it felt great to solve a small problem I had. (I hope I'm not shoving Gopen in the article too many times, but it turned out to be very relevant for this topic.)

### Building a Good "Product"

This is quite an interesting point raised by Lane. It's that one of the advantages of building CLIs or building for developers is that you can do a better job building a "product" or at least doing work that an engineer would care about because, on the other hand, non-technical people will judge how good of a product your work is rather than the engineering quality. It's unfair but true.

## Static Typing

No need to say much here... Lane, Prime, myself, and a big bunch of other people are now calling everyone to go for statically typed languages. I've written a couple of articles on that matter for you to check out:

* [Typing and Tooling](/posts/typing-and-tooling/)
    
* [TypeScript: a Beginner's Perspective](/posts/typescript-a-beginners-perspective/)
    

## Functional Programming is Hard

"Why isn't OCaml more popular?" Lane asks. Prime says because FP is harder, and I do agree. So, allow me to expand on that. In my view, common C-style languages have very simple concepts that are associated with imperative programming like loops, if-else statements, etc. Anything from there is just a bunch of abstractions on top of these simple concepts, an example of which is classes and OOP in general.

FP, on the other hand, has a larger number of unique concepts that you need to study before implementing in code. The most common of these concepts, which Prime mentioned, was recursion. Another one is function composition, which turned out to be one of my favorite ways of building software. Then there is currying and monads and a whole bunch of other stuff. There's a lot to learn, and I won't deny it. However, the advantage of these "advanced" concepts is that they cause the code to be more concise and arguably simpler.

While my current favorite language is Go, I'm still looking forward to playing with a functional language on the side after I got through the initial part of Go's learning curve and am developing comfortably in it.

## Conclusion

That was such a fun episode to listen to with an insightful discussion and a lot to learn beneath all the fun and memes. Big thank you to Lane and Prime! I am glad to start writing down stuff from other content because that helps me capture as many insights as possible and contemplate them at a deeper level vs. passive listening.

Thank you for reading, and I hope you found it insightful and fun.
