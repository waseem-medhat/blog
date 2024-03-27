+++
title = 'Separation of Concerns, Locality of Behavior, and Javascript'
date = 2024-03-27T13:05:23+02:00
tags = ['JavaScript', 'Frontend', 'Backend', 'Learning']
categories = ['Blog']
images = ['/img/serverlessmeme.png']
+++

In this article I will share my personal take on the new full-stack JavaScript frameworks with respect to these two concepts in the title and why they are important factors in my tech preferences.

There is a lot to unpack here, so this is enough of an introduction... Let's get right into it!

## The State of Things

Full-stack JS frameworks like Next, SvelteKit, etc. are probably the hottest thing in the web right now. If I'll (over-) generalize their premise, it would be that they extend front-end frameworks (React, Svelte, etc.) to introduce back-end functionality so that both sides share code together, bringing many benefits to the developer experience and ease of deployment thanks to serverless-based products like Vercel.

These kinds of frameworks are challenging the current ways of doing things, which I'll generalize into two categories:

1. The **Jamstack**, which involves total decoupling between a front-end application and a server-side one, usually a JSON API.
    
2. The **"back-end" languages** like Go, Python, etc., which make full-stack applications using templating engines to dynamically render HTML on the server. They usually call these kinds of apps "monolithic."
    

The details of how full-stack JS frameworks challenge these two categories are the actual meat of this article, so bear with me as I explain some stuff.

## The Terminology

There's nothing like a bunch of technical terms that you can throw around in conversations to give an air of intelligence and pretentiousness.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711370690081/c23e4f77-6763-44b6-8212-c9fafbe33e7f.png align="center")

### Separation of Concerns (SoC)

> "\[...\] a design principle for separating a computer program into distinct sections. Each section addresses a separate concern, a set of information that affects the code of a computer program." - [Wikipedia](https://en.wikipedia.org/wiki/Separation_of_concerns)

I think things can be more clear and concrete through an example. One of the most prominent architectures (in the context of full-stack web apps) that follow this SoC principle is MVC (model-view-controller). This is what's typically used by back-end frameworks in the 2nd category I mentioned earlier, where the program is structured around *tasks*, so you get a file/directory for routes and another for templates, etc. Another example is separating HTML, CSS, and JS each into their own files.

### Locality of Behavior (LoB)

> "The behaviour of a unit of code should be as obvious as possible by looking only at that unit of code." - [Carson Gross](https://htmx.org/essays/locality-of-behaviour/)

As stated in the quote and the linked article, LoB is about making a unit of code reflective of the whole behavior. Since this article comes from HTMX's author, it explains that adding HTMX tags to an HTML element achieves LoB because the element's code now shows you the request it triggers and what elements it will swap. So, while adhering to SoC requires splitting tasks into separate pieces of code, adhereing to LoB means you combine the tasks together for each *feature or component*, and this is where the two principles are in conflict.

I already mentioned HTMX as an example. Another popular one is TailwindCSS, which achieves LoB by inlining classes to apply CSS rules to HTML. You know what else shares this principle? Yep. Full-stack JS frameworks.

## Locality of Behavior in Full-Stack JS

One particular point in which the new frameworks challenge both categories of typical web development is that the new frameworks are the most *pro-LoB* among them all. They have taken the component model that worked on the client side for years and made it so that the same component can be rendered in both places as necessary and even do any necessary back-end logic.

Now, all you have in your codebase is components, features, parts of your app, whatever you wanna call it. The component will be rendered on the server if it's opened for the first time. It will be rendered on the client during client-side routing. It will fetch data from an API endpoint or from a database via an ORM. You see, this is as LoB as it gets.

Is this good thing? Are the new JS frameworks better? Well, it depends. Always does. But putting aside any business constraints like, say, the job market availability of a certain technology, the choice between a SoC-focused technology and a LoB-focused one, in my humble opinion, has a very large subjective component to it (pun unintended), and from now until the end of the article, I will discuss that subjective part from my personal view.

*Spoiler alert: full-stack JS frameworks aren't for me (at least in the current stage of my life and way of thinking).*

## My Take

### Clients, Servers, and HTTP

Let me start with a quote that may have single-handedly caused me to write this article:

> "I don't like it when I have to go and write a normal GET request or I have to write a normal POST request, and I have to use HTTP verbs like we did back in the MERN stack days." - [Ben Davis](https://youtu.be/4XctkLE3MuM?si=o82VmGMKZ_Ai9oX2&t=765)

This statement is so interesting for me for two reasons:

1. Though I didn't watch a ton of his content, I know Ben's an ex-gopher. He used to do Go with SvelteKit, and now he switched to be all-in with the full-stack JS stuff. So he has been where I am now, but wasn't satisfied and moved on.
    
2. What he says he doesn't like in this quote is *exactly* what's making me happy writing Go and dealing with HTTP that way.
    

Around 6 months ago, I wrote an article with the title [React Rant (+ Should I Be a Backend Dev?)](https://wipdev.hashnode.dev/react-rant-should-i-be-a-backend-dev) which, as you may have guessed, includes the frustrations I had with React and thinking that maybe I should try a "real" back-end language. I usually make these decisions based on some gut feeling, which you might see if you read the article. However, after 6 months of Go, I believe I made the right decision.

By using Go as a back-end language, I learned a lot about servers, HTTP, and the way the web works in general. I like it a lot when the technologies I'm working with correspond directly to web standards and concepts that I can look up on MDN. A very recent example in my journey was HTTP cookies. Without going into too much details, the Go standard library `http` package has a `Cookie` struct type whose fields are the same as the [`Set-Cookie` attributes as shown on MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie#attributes). The abstraction here is extremely minimal.

Overall, Go, like many back-end languages, keeps you conscious of the fact that you have clients and servers that interact with each other via HTTP. On the other hand, a common theme in YouTube content discussing full-stack JS frameworks is that the line between the client and the server is blurrier than ever. Moreover, people like Ben are actively moving away from the "client-server" way of writing code, and that doesn't sit right with me.

To be clear I'm not against LoB at all. I loved the component model in JS frameworks, and in Go, I use Templ with Tailwind and HTMX which separates the templates into components with LoB. However, the separation remains clear between the client and the server. HTMX itself has HTTP and the client-server relationship as strong parts of its philosophy. This is my favorite way of doing things currently.

### We Think Differently

I noticed that most tech-related arguments I see or engage with can be somewhat attributed to what I read and then discussed in [this article](https://wipdev.hashnode.dev/article-3-tribes-of-programming) about our leaning toward one of 3 categories. How so? Simply because full-stack JS advocates - at least the ones I know - seem to be of the Maker type. They're product-oriented. The new framework simply abstracts away the client-server architecture so that you can focus on writing features.

With the new frameworks, you no longer have to add a new model in the models file, a controller in the controllers code, and write a new route and how it'll respond to different HTTP verbs, etc. You just create a new directory with a "page" component and now you got yourself a new route in which you can write any logic you want - data fetching, auth, redirection, whatever.

I like knowing how things work, and I dislike having too much abstracted away from me. If client-server is how web applications work, then client-server is how I want to work. Knowing how things work made me good at learning new technologies and debugging most issues I run into with relative ease. React as an SPA framework, and all the new full-stack frameworks took that away from me. Debugging was hard and trying to solve problems without studying *their way* gave me too many footguns. I simply didn't enjoy working that way.

## Strong Opinion, Weakly Held

To conclude, I'd like to say that I've grown to believe that most preferences we have in tech are subjective. So, I always try to analyze my views as well as others' with that in mind. With respect to the discussion at hand, all I can say is that I strongly believe in what I just shared, and I'm willing to accept that this view is colored by my own experience and what I want to learn at this point in my life. Also I'm willing to accept that this may (or may not) change in the future as I write more software.

As always, this was another thinking-out-loud kind of article, and I hope you appreciate the food for thought. Thanks for reading!
