+++
title = 'Gopen'
subtitle = 'A simple CLI to quick-start coding projects'
date = 2023-11-04T14:13:31+02:00
categories = ['Projects']
tags = ['Go', 'CLI']
images = ['/img/gopen.png']
+++

Source code: <https://github.com/wipdev-tech/gopen>

The premise of this command-line utility is to save an editor of choice and a
list of aliases for your local development projects instead of "polluting" your
system-level configs (e.g., `.bashrc`). Then, Gopen command will `cd` into that
folder and open your editor of choice.

I used it as a dogfood solution to the relatively straightforward problem of
having to navigate to a project folder and open Neovim every time I open a
terminal. Plus, it would serve as good practice with Go.

## Installation and Usage

[Check the project's GitHub repo](https://github.com/wipdev-tech/gopen) for the
source code, pre-built binaries, and any relevant documentation. The rest of
this article will be more of a technical walk-through plus my thought process
and learning from the project.

## Technologies

Gopen is written entirely in Go and its standard library. Go seems like a great
tool for developing command-line utilities like Gopen since it's simple to
write, fast to run, and compiles to a binary without the need for the source
code and an interpreter.

I figured a simple CLI with a size of 2 MBs isn't too favorable. So, I used
[TinyGo](https://tinygo.org/) to compile the binaries in the GitHub releases.
Even with stripping, TinyGo does make a significant difference in the size of
the compiled binaries.

## Collaboration

I shared the project in Discord servers to ask for feedback, and thankfully, it
got picked up by other users. One of them even gave me excellent feedback and
then collaborated with me in the project.

## Skills

This project helped me learn a lot about Go's standard library:

- Handling command-line arguments
- File I/O
- JSON marshaling/unmarshaling
- Go doc comments on functions and packages
- Testing with `go test`
- Linting with `golangci-lint`
- Compiling for multiple operating systems
