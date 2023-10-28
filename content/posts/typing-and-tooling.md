+++
title = 'Typing and Tooling'
date = 2023-10-28T18:49:08+02:00
draft = false
categories = ['Blog']
series = ['Clojure vs JavaScript']
tags = ['Clojure', 'JavaScript', 'TypeScript', 'Go', 'Learning']
images = ['/img/lsp.png']
+++

These two topics have become very important factors that influence my developer experience when working with a programming language. This is because when you're coding in a certain language, you are buying into its tooling ecosystem one way or another. So, they played a very important role when I was comparing and contrasting Clojure and JavaScript in my head, which I will talk about here.

Just to set the context, by "typing" here I mean the type system, and by "tooling" I mainly mean the editor support and LSP (although the word can be much more general than that). If you don't know much about LSP, you might think that the type system and editor support are unrelated. I'll explain everything and hopefully, it'll make sense why both topics are in a single article.

## Static Typing

Strictly speaking, "static" and "strong" type systems have different meanings: statically typed languages have a compiler that does *static analysis* of the code, while strongly typed languages mean that they are strict with their types and don't allow things like type coercion as much as weakly typed languages. For the sake of this discussion, I will only discuss static typing since that's the most relevant to the topic (but I like strong typing as well).

I became a fan of static typing when I took a programming course around 3 years ago. The Standard ML language was used by the instructor to teach students about static type-checking (among other things). Having a compiler that checks if something doesn't conform to a certain type or pattern clicked with me even when all my time before this was spent with dynamically typed languages like R and Python.

If you're the least bit familiar with the JavaScript ecosystem, then you can already guess that I am going to talk about TypeScript, and you'd be right. But first, let's talk LSP.

## LSP

The [Language Server Protocol](https://microsoft.github.io/language-server-protocol/), put simply, is a client-server protocol, which is kinda like HTTP except that the server is a "language server" and the client is your editor. The language server's job is to provide the editor with information about your code so that the editor can show autocomplete suggestions, jump-to-definition or jump-to-references functionality, type-checking errors, etc. LSP was developed by Microsoft to make an IDE-agnostic way of supporting a certain language with IDE functionalities, and almost all modern editors have LSP clients now.

How does this tie in to static typing? Well, based on my experience, statically typed languages are associated with better language servers, which I guess makes sense because compilers use types to "know more" about the code in a certain project. On the other hand, interpreted languages cannot know about a lot of errors until runtime, and they have (mostly) no way of knowing what possible properties a certain object can take, etc.

I have grown to greatly appreciate the importance of a good language server showing me compile-time errors right in the editor without needing to switch windows or compile/run the code myself at all. Because of that, I now very strongly prefer statically typed languages.

I hope that I did a good enough job explaining these concepts and that now the context is clear for discussing the languages themselves.

## TypeScript

So, while JavaScript is technically a dynamically typed language, TypeScript has been introduced as a JS superset so that it adds extra types and static type-checking on top of the vanilla language. I consider learning and using TS in my projects to be an absolute plus in my front-end journey because this is the first time I wrote statically typed code professionally (any other statically typed language I learned before was just part of my hobbyist learning).

TS does a great job protecting us from the hot mess that is JS. I consider the JS type system to be dynamic to a *terrifying* degree, and we've all seen the memes about that. Also, thanks to having more specific types for HTML elements, events, web APIs, etc., the TS language server can give you a richer developer experience through better autocomplete, tooltips with documentation and function signatures, and more informative error messages.

So, more predictable code, plus more "smartness" from your editor in tooltips and autocomplete... What more could you ask for? I wrote a slightly more detailed article, [TypeScript: a Beginner's Perspective](/posts/typescript-a-beginners-perspective/), that you can check out if you're interested in TS specifically.

## Clojure

Clojure, unlike TS, is a dynamically typed language. This is probably the #1 deal breaker for me. However, I wouldn't say that it is "like" JavaScript in this case because Clojure is kind of special and has some unique features that most likely are considered by Clojurists to make a better approach than static typing.

First, Clojure (and Clojurists) strongly claim to be very data-oriented in the sense that they prefer dealing with data directly, minimizing the need for abstractions into types or classes. I didn't use Clojure professionally, but I do think this data-oriented approach is better than an object-oriented one with classes and inheritance. However, I am still pro-types because types make the code a little bit easier to understand and reason about. Also, static typing means that language servers can get more information about the code, so you get better autocomplete and diagnostic messages in your editor.

Another interesting aspect of Clojure development that minimizes the need for a compiler is interactive, or REPL-driven, development. That works by writing code while having a REPL (console) open all the time so that you evaluate individual pieces of code by sending them to the REPL. This makes it easier to quickly test individual functions instead of recompiling the whole application each time a single function/module is modified. I have been using that approach for years in my statistical programming with R, so I can appreciate that Clojure development works the same way. However, as time went on, I gravitated more toward static typing and compilers for the reasons I already mentioned above.

## A Final Note

At the current point in time, I consider this to be the last [Clojure vs. JS](/series/clojure-vs-javascript/) article. This is because my Clojure journey has come to an end (or a temporary pause, at least). The same kinda goes for JS, but as a web developer, I'm sure I'll still interact with JS one way or another even if my focus now is on the backend.

So, my focus now is almost completely on Go, and that feels like a step in the right direction because it's a compiled, statically typed, and strongly typed language. I'll sure talk more about Go in future posts, so I won't say too much now except thank you for reading till the end!

---

The cover photo is a screenshot of language servers installed on my machine as shown by Neovim's [Mason](https://github.com/williamboman/mason.nvim) plugin.
