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
folder and open your editor of choice. I used it as a dogfood solution to the
relatively straightforward problem of having to navigate to a project folder
and open Neovim every time I open a terminal. Plus, I figured it would serve as
good practice with Go.

[Check the project's GitHub repo](https://github.com/wipdev-tech/gopen) for the
source code, pre-built binaries, and any relevant documentation. The rest of
this article will be more of a technical walk-through plus my thought process
and learning from the project.

## Technologies

Gopen is written entirely in Go and its standard library. Go seems like a great
tool for developing command-line utilities like Gopen since it's simple to
write, fast to run, and compiles to native OS binaries without the need for the
source code and an interpreter.

I figured a simple CLI with a size of 2 MBs isn't too favorable. So, I used
[TinyGo](https://tinygo.org/) to compile the binaries in the GitHub releases.
Even when comparing stripped binaries, TinyGo does make a significant
difference in the size of the output.

Finally, some small amount of automation was done with a makefile. The file
simply contains some commands for formatting, testing, linting, and compiling
the three binaries.

## GitHub & Collaboration

One thing I thought about was that the tool may be interesting for other people
to use, so I paid as much attention as possible to the GitHub repo. I used the
`README.md` to provide clear documentation on how to install and use Gopen.
Pre-compiled binaries (for Linux, Windows, and MacOS) are also available in the
[releases](https://github.com/wipdev-tech/gopen/releases) page for direct
download and use.

I shared the repo in Discord servers to ask for feedback, and thankfully, it
got picked up by other users. One of them even gave me excellent feedback and
then collaborated with me on the project in both issues and pull requests.

## Skills

As a portfolio project, Gopen demonstrates these skills with Go:

- Handling command-line arguments
- File I/O
- JSON marshaling/unmarshaling
- Go doc comments on functions and packages
- Testing with `go test`
- Linting with `golangci-lint`
- Compiling for multiple operating systems
- Makefiles
