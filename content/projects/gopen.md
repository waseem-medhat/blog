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

## Skills

This is my first Go project ever, so it served as a good introduction to many
things in the Go language and standard library:

- Handling command-line arguments
- File I/O
- JSON marshaling/unmarshaling
- Go doc comments on functions and packages
- Testing with `go test`
- Linting with `golangci-lint`
- Compiling for multiple operating systems
