+++
title = 'Elixir: the Only Sane Choice in an Insane World?'
date = 2024-10-01
categories = ['Blog']
images = ["https://i.imgur.com/4LMG6ia.png"]
+++

The title of this article is ~stolen~ inspired from a [talk by Brian
Cardarella](https://youtu.be/gom6nEvtl3U?) (except the question mark). While I
won't exactly review the talk itself here, this will be my own spin of what it
is about: why I find Elixir to be such a great language after working with it
for a few months, and why it made a lot of sense when other languages and
ecosystems didn't.

I will individually tackle some general ideas about Elixir in light of my own
past experiences and my current interactions with the language, which may or
may not be different from other people's.

## Functional Programming

This is probably the first thing that comes up when Elixir is mentioned, and
surely it does bring many ideas from FP. For example, most of the code I wrote
so far is functions that transform data structures and are namespaced in
modules. Data structures are immutable, and that forces you to unlearn some of
the imperative ways of doing things. Pattern matching is also a big part of
writing idiomatic code, including writing multiple function clauses, i.e.,
multiple function definitions with the same name but match different argument
patterns.

From a personal perspective, I've always enjoyed working with functional
languages. I like the simplicity of working with functions and data. Also, when
you look at back-end development as a process of pulling some data, applying
some transformations to it, and then sending it somewhere, I would say that FP
matches this description perfectly. Not to mention that immutability makes the
code more predictable and prevents certain bugs. Also, the pipe operator (which
I've liked since I learned R) and pattern matching are my two favorite language
features ever.

Another interesting point about Elixir is that it works well for web
development in comparison to most functional languages. Among the ones I tried
so far, Elixir has the least amount of that academic or mathematical feel that
people associate with FP. I think this is due to many factors (and they will
become clearer as I explain more below), but the most important one in my
opinion might be the creator's background and objective. José Valim was a Ruby
on Rails developer and created Elixir to leverage the Erlang VM. So, after
working with the language, it shows that it was built with web development at
the front and center.

## Dynamic Types

I admit that I ignored Elixir for a long time because I was (and in a sense
still am) a strong advocate of static and strong type systems. Types can be a
form of documentation, giving more information to compilers and language
servers and improving developer experience. More importantly, they prevent a
whole class of bugs like catching a typo in a struct field or something that
may end up being null while you assume it isn't.

To my surprise, I am having a good time writing Elixir despite the lack of
these things I've grown to expect after using TypeScript and Go. I think this
is because the major advantages of static typing and LSP are achieved in Elixir
through other means. For example, Phoenix is set up with auto reload, and the
compiler is pretty fast and gives you instant feedback with errors and
warnings. Also, pattern-matching (via `case` expressions or function clauses)
can replace types as means of communicating assumptions and making assertions
about data.

The great news is that type-checking is currently being gradually added into
the language. At the time of writing this, the current version of Elixir is
1.17 which was the [first version to add these
types](https://elixir-lang.org/blog/2024/06/12/elixir-v1-17-0-released/). Even
better, it was recently announced that [LSP support is also being actively
worked
on](https://elixir-lang.org/blog/2024/08/15/welcome-elixir-language-server-team/)
which I believe should only make the experience of writing Elixir even more
enjoyable.

## Phoenix

The 2nd primary reason that got me curious about Elixir, other than FP, is
Phoenix, and this is probably how many people hear about Elixir for the first
time as it is considered one of Elixir's "killer apps." I got into Phoenix
after using Go which has a different approach of building back-end apps by
starting from a blank slate and adding relatively low-level primitives (most or
all of which are from the standard library) as needed. So, it was interesting
to try Phoenix is a more opinionated and fully featured framework.

There was an initial bump trying to make sense of the framework's individual
pieces and directory structure. But thanks to the phenomenal
[documentation](https://hexdocs.pm/phoenix/overview.html), things became
clearer and I started becoming productive in the framework. Overall, Phoenix
and the base language complement each other for a quite nice development
experience. Ecto is also a cool library that handles the SQL side of things
like creating schemas, building queries, etc., and it has this interesting
concept of changesets that handle validation of data, usually before committing
it to the database.

One special thing about Phoenix is its strong support for front-end development
with its inclusion of TailwindCSS and ESBuild out of the box and even more so
with LiveView. I found LiveView to be both ergonomic and efficient as a way to
add rich client-side interactivity while still keeping things server-driven. I
also find it interesting that Phoenix feels like a nice middle ground between
the highly opinionated frameworks like Django and the JS style of picking
various independent libraries and gluing them together. You can clearly see the
individual pieces of Phoenix like Plug, Ecto, etc., but they are seamlessly
integrated with sane defaults to make for a coherent framework for
production-ready back-end or full-stack development.

## Simplicity

There are multiple loosely-related ideas that I want to discuss here about the
simplicity I seek in a language, especially at an ecosystem level, and I think
these ideas should become clearer by explaining the complexities that made me
less satisfied with other languages previously.

I went through some burnout due to the constant changes in the JS ecosystem,
not to mention the frequent flame wars and other drama around it in the
community, I was looking for a simpler, more stable ecosystem, one that doesn't
change much over time. I want my language to get out of my way while I dive
deeper in *concepts* instead of spending most of my time catching up with some
new syntax that introduces a slight variation of the same thing (that or
battling FOMO if I chose not to catch up).

Between JS and Elixir, I did Go for a year. When I learned it from
[Boot.dev](https://www.boot.dev/) and YouTube, it was appealing as an
increasingly popular back-end language with a great focus on simplicity and
backwards compatibility. The projects that I saw and built were simple and
effective, and the standard library allows you to go a long way without
reaching for 3rd party packages. Unfortunately, writing full-stack monoliths is
only a young trend on the internet. In real life, Go is mostly used in
microservice architectures and is heavily associated with cloud (e.g., AWS)
services, Kubernetes, etc. So, while the Go ecosystem is technically stable and
simple, it still brings with it a lot of complexity with it in the architecture
and tooling that surrounds it.

After building all this context, let me share this table from "Elixir in
Action" by Saša Jurić:

![Elixir in Action table](https://i.imgur.com/qnJ4UW3.png)

Elixir, or more precisely the BEAM VM, brings a lot of power and efficiency so
that you can do more with less. José Valim once said in an interview "you only
need your programming language and a database" and that resonated with me. This
means that I can focus on as few technologies as possible and focus on becoming
really good at them instead of having surface level knowledge about many
things. This also means that Elixir can be a great choice for building a
business because the ecosystem is powerful enough to support most or even all
of its needs.

In short, the appealing simplicity in the Elixir/Erlang ecosystem for me is
that I don't have to glue together tons of 3rd party libraries (like JS) or
microservices (like Go). Both the language and the underlying VM are stable,
reliable, and worth investing my time and effort into.

## Documentation

Since documentation is a real first-class citizen in Elixir, I had to give it
its own dedicated section. This is one thing that I deeply appreciate in the
language. Both Elixir and Phoenix have some of the best documentation I've ever
seen for any piece of software. Not only is there a rich explanation attached
to every function, module, and error message, there are also separate guide
pages like the ones in [Elixir](https://hexdocs.pm/elixir/introduction.html)
and [Phoenix](https://hexdocs.pm/phoenix/overview.html). These guides can be
read start-to-finish like books, and they even have EPUB versions which I did
load in my Kindle.

It's true that almost everyone would agree that writing documentation is a good
thing, but it's rare to see *this* level of investment at a language level that
grows to be one of the community's core philosophies. So, yes, while
documentation is by no means something that I'm discovering now, writing Elixir
and being in touch with its community motivates me to improve my ability to
document my code.

## Final Notes

This concludes my long essay about my newfound excitement for Elixir: a
language that is functional (but accessible), simple (but powerful),
well-documented, and overall very fun to work with. I am nowhere near mastering
the language yet, so I have a lot to explore and dive deep into, whether it is
the language itself or the underlying Erlang VM patterns for concurrency and
fault-tolerance. But I am looking forward to doing all that, and I plan to
develop and maintain multiple open-source projects with it, and of course I am
gonna rave about it in future articles.

Thank you for reading!
