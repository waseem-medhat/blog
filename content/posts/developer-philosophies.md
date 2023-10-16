+++
title = 'Developer Philosophies'
date = 2023-09-29T19:37:57+03:00
draft = false
categories = ['Blog']
tags = ['Clojure', 'JavaScript']
series = ['Clojure vs JavaScript']
images = ['/img/js-fw.png']
+++

All previous articles in this series discussed very basic language differences between Clojure and JavaScript based on my learning so far. I will switch to a different set of topics in this article, discussing some philosophies adopted by each developer community. Although each developer is always free to form their own opinions, what I discuss here is my observations of what is commonly embraced or encouraged by most developers in each community.

## Interactive Development

This method of development (aka REPL-driven development) is encouraged by Clojure and its community. The idea is that during development you have a REPL/console that is running, you connect your IDE to that REPL, and you start to interactively evaluate expressions in your code as you go. For example, you write a function and then start calling it on test values to ensure the output is returned as expected. Another example is when you have a running web server that relies on some functions and then you redefine those functions without needing to restart the server.

I guess that way of development comes naturally with Clojure or functional programming in general because most of the code you write consists of individual, mostly pure, functions that can be evaluated and tested individually. This method of development is also very common in R where, most of the time, the whole purpose of using the language is interactively analyzing data instead of running an app or a script from the shell. Since R was my first language, I feel at home with REPL-driven development in Clojure, and I am looking forward to seeing how Clojurists use that in real-world settings.

As far as I know, such a concept does not exist in the common JS workflows. Since the code is meant to run start-to-finish by a browser or a Node runtime, I have to `console.log` any value I want to test. I wouldn't go as far as saying it's a horrible approach or anything, but it takes writing extra code and switching from your editor/IDE to the browser. So, it's slightly more time-consuming, and it breaks the developer's flow more often. Plus, I always forget some `console.log`s scattered through the project and have to clean them up.

## Roll Your Own Stack

While the JavaScript community maintains its focus on frameworks, most of the Clojure community seems to be focused on building apps from a set of stable low-level libraries. If you look around for web development in Clojure, most recommendations will be for libraries and not full-fledged frameworks. I wanted to ask to confirm that this roll-your-own-stack approach was actually used in practice, and I received the reply "It's the Clojure Way."

There are two positive implications of following that philosophy. One is the reduction of dependencies because you get to use the libraries that you need to and nothing more. this is opposite to the common framework approach followed in JavaScript where you download an opinionated set of libraries, file structure, and boilerplate before you even write a single character in your code. I often mention in articles that I don't like having many dependencies in my code, and I wrote a [full dedicated article about it](https://wipdev.netlify.app/posts/dependencyphobia).

The other benefit is that dealing with lower-level pieces of code is more educational than frameworks. So, to take backend development as an example, you get an idea about how things like HTTP and routing work instead of just superficially knowing how to write the "Django code" that does X. It's not all positive, though. There is a reason people follow frameworks, and that's because a lower level of programming requires more knowledge and work on the developer's end. I am not experienced with backend, and I am not experienced with Clojure either. So, it takes me some considerable effort to add any basic new feature.

## Noise

It probably wouldn't be an overstatement to say that JavaScript is the most popular programming language these days. Also, JavaScript is the language with the most buzz around it. One factor in play here is the huge number of frameworks, so there is always something new to talk about. Also, JS's popularity made it an integral part of the software industry, and businesses nowadays thrive on attention. It's common nowadays that a company "sponsors" a framework by hiring one or more of the authors/maintainers to work on it full-time. So, now you have marketing adding to the noise.

It's not just the frameworks that keep coming out or getting breaking updates, but also the drama around certain topics from time to time if you try to follow JS news on social media. By the time I wrote this, a couple of weeks had passed since two heated discussions happened in the tech space (as far as I know): one about Bun and another about DHH's strong opinions against TypeScript. (I won't even share links - if you don't know, be happy about it.)

The Clojure community feels like an extreme opposite of JS's. The community is, comparatively, very quiet and has a tiny online presence. &gt;90% of the content I found related to Clojure are talks in Clojure/FP conferences. On one hand, I appreciate the near-lack of drama (I noticed some but in very isolated places I never interacted with) and the complete lack of noise. On the other hand, there is a significant scarcity of educational Clojure content. So, all I've got to do is either read the official documentation for the language or the package, which may or may not be helpful, or ask around in Discord/Slack for everything, which I don't find very pleasant or time-efficient.

## Conclusion

So, these were some of my observations of the Clojure and JS communities and their philosophies in programming. I can't say I am strongly leaning towards either side, but I found it interesting to compare and contrast the two. I hope you found that interesting as well.

---

Cover image source: [Every day we stray further... we get a new JS framework! : r/ProgrammerHumor (reddit.com)](https://www.reddit.com/r/ProgrammerHumor/comments/8doavn/every_day_we_stray_further_we_get_a_new_js/)
