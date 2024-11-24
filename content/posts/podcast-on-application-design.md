+++
title = '[Podcast] On application design'
date = 2024-04-19T20:02:13+02:00
tags = ['Backend', 'Go']
draft = false
categories = ['Blog']
series = ['Content Reviews']
images = ['https://i.imgur.com/w7JiMpm.png']
+++

I thought it might be a good idea to review this interesting [Go Time podcast episode](https://changelog.com/gotime/102) where Mat Ryer, Peter Bourgon, Kat Zień, and Ben Johnson talk about application design. At the time of writing this, I'm working on a couple of apps in Go which were large enough for me to start worrying about design. So, the topic of this show is something I'm actively invested in.

Without further ado, let's get into it!

## Context Matters

The first important point discussed here is that the design should primarily be guided by the context in which we work. For example, designing an application as a single, maybe beginner, developer is a different thing from designing an application in a large company with multiple teams. Even in the context of a large company, the design in the first stages should be different from later stages when the application grows or gets more user feedback.

They also point out that ignoring contexts can be the source of debates or cut-and-dried opinions about what should and shouldn't be done. Like many things in life, "it depends." Always does. I'd say this is an important point to be conscious of not only in application design but almost anything else in development

## Global = Bad

The discussion moves from contexts to global state, which everyone agrees that it should generally be avoided. Peter speaks specifically that, in Go, packages should only declare functions and types, and the main entry point should be where global state is initialized if needed. Once you do that, the application becomes more predictable, easier to reason about, and less prone to a number of bugs. While this is mentioned in the context of Go, I think the principle should apply to the majority of languages.

Another point raised by Peter as well is that the cost of the extra verbosity caused by avoiding global state is effectively negligible in a long-living program. Personally, I like this way of looking at it, and I think it suits one of Go's philosophies which is being as explicit and anti-magic as possible even if the price to pay for this is making the code less concise.

## "Run" Function

This one is probably more Go-specific, but maybe it can somehow be adapted in other languages. Mat here says that instead of running stuff in `func main()`, he puts the logic in a `run()` function that returns an error. That way the function can be tested, plus the code that prints errors to standard output would be written only once. I never thought about that but I find the idea quite interesting and might try it in the future.

## Don't Program for the Future

> \[...\] at every step of the way don’t write more program than you need at that step.

Everyone on the podcast agree that we should start simple with our programs, and the design and architecture stuff should come later only when it's needed. That has been my own philosophy while coding, and I'm glad to see some people with far more experience than me agreeing with this philosophy.

Mat speculates that when we look at a large Go project we may think that this structure was there from start, but most likely it wasn't. He says that projects should *"organically grow"* into a certain structure, an expression that I absolutely love. He also said that it's totally normal for people to correct or redesign code after discovering a problem that needs solving.

Another nice point raised by Kat is that some things can be anticipated with experience. In other words, having experience makes it easier to account for some problems before they emerge. But if such experience doesn't exist then - like everyone said - simply keep writing until a need for a redesign is there. Peter also talks about this in terms of building abstractions, saying that "abstractions have to emerge from the program."

For me this is the highlight of the podcast episode, and I think they would agree with me as well since the topics they discussed over the show's runtime lead back to this same idea: start small and let the system organically grow into the design it needs.

## Delete Your Code

Another very good advice, maybe because it applies to me too well, is to be comfortable with deleting or rewriting code. The idea is that when you're starting a certain project, you do your best to work with the current information you have about the domain problem at hand. But when there is new information, it should be easy to refactor or delete any parts of the code. I say it applies to me because I have no problem deleting stuff or running `git reset --hard` almost to a fault.

While Peter put the idea in a perspective of adaptability to new information or new problems, Mat puts it in a perspective of distilling the code and making sure it has nothing more than it needs. He even says a package can be rewritten from scratch after getting a clear sense of what it needs. "The art of writing is rewriting."

## Microservices Design

That part of the podcast focuses on multiple ideas related specifically to microservices, the first of which is mentioned by Ben is having too many packages or microservices with no clear structure, to a point where there are packages with no other purpose than to allow other packages to communicate or "to make the compiler happy." Mat emphasizes that we shouldn't be writing for compilers but for humans.

Another idea is related to consistency across the different microservices. Kat recommends consistency and even using code generation to give microservices the same structure. Having a consistent structure makes any service easier to navigate, even if there are so many of them in a project. It also makes maintenance and deployment easier and abstracts away some implementation details, reducing the barrier to entry. But this assumes that all microservices are built in the same language. Otherwise, it wouldn't be great to force multiple languages into a single structure.

Peter (and Ben) goes in the opposite direction from Kat in a sense that he tied the design of microservices to [Conway's law](https://en.wikipedia.org/wiki/Conway's_law). It's the idea that microservices solve an organizational problem, not a technical one. His view is that every microservice should be owned by a team so that any single programmer doesn't work on more than one microservice. That way, the design and implementation of a microservice should be up to the team who owns it. Kat argues that this approach may not be future-proof or scalable especially in large companies.

## Hex Architecture

The conversation moved from microservices design to the [hex architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)) which, as Kat put it, is a pattern that separates an application's parts like the business logic, the third party logic, the application/framework code, etc. This separation makes each part easier to maintain, change, and test. Peter also describes it as layers of onion where the core is the business logic and you go outward to the outermost layer which is the network layer (e.g., gRPC), and there are explicit boundaries between them.

A question that came up by Mat around this topic is about handling the conversion of struct types between layers. He first talks about either direct type-casting or having a method on a struct to convert it to another type. Then Kat says that a better solution is having marshaling (utility) packages that are available to the service because having a method on a struct means that the struct "knows" about the other type representation, which it shouldn't.

This leads to the question asked by Peter about "how philosophically strict you wanna be in your application." Because you could choose to use one type across all layers. This violates the layering principle of the hex architecture but could be justified from a practical standpoint. On the other extreme, you could write a specific type for each layer. Choices could be made across that spectrum, and Peter says that the project and company size could be a deciding factor, where bigger ones will probably make it a better choice to be explicit and make types and marshaling functions for each layer.

## Performance

Ben raised a point that he may "violate" the hex architecture and mix business logic with other layers which improves performance. In that regard, Mat says that he prefers readability and maintainability over performance as long as performance is not really an issue. The same idea was expanded by Kat when she said that sometimes people focus too much on "micro-optimizations" which have little impact on performance. An example of this is when Go developers actively avoid using `defer` because it's slightly slower.

Another concept to prioritize over performance is transactional integrity. It's the idea that, in terms of business logic, if there is a single transaction that require multiple calls then they can be grouped together, and you can have the performance benefits of such grouping. Otherwise, if it's a group of independent transactions then they should probably be separated. As always, these decisions are always context-dependent.

## Concurrency

The next discussion is about how to take concurrency into consideration with respect to application design. The general sentiment is to not lean into it. When it comes to packages, they recommended avoiding concurrency so that it would be the caller's choice. In other words, a package's functions should not use concurrency, but they should be safe to be executed concurrently if needed.

Another point is that concurrent code should be kept in one place (e.g., `func main`) as Mat said and Peter expanded on. The idea is to keep everything direct, sequential, and unambiguous. But since concurrency breaks that pattern, it should be as localized as possible to prevent having magic in multiple places.

Kat then talked about that when the services are small, there is already no need to do anything concurrently in any service because it does one thing. In that case, the system in general might use concurrency, but not the individual services that are single-responsibility in nature.

## Conclusion

When I listened more attentively to this episode and tried to review it in written form, I realized that it was such a rich episode full of great nuggets of information, and it shows in this article's length.

I would say the best takeaway from this episode is to be comfortable starting with contained and readable code unless you need to change that. Let your code organically grow into the design it needs. Break the code into services only when it gets big enough. Don't try to optimize performance at the cost of readability or transactional integrity (except for performance-critical apps).

I really enjoyed writing about this episode, and I hope you did too. Thanks for reading!
