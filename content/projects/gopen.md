+++
title = 'Gopen'
subtitle = 'A simple CLI to quick-start coding projects'
date = 2023-11-04T14:13:31+02:00
categories = ['Projects']
tags = ['Go', 'CLI']
images = ['https://i.imgur.com/To9GQkL.png']
+++

The premise of this command-line utility is to save an editor of choice and a
list of aliases for your local development projects instead of "polluting" your
system-level configs (e.g., `.bashrc`). Then, Gopen command will `cd` into that
folder and open your editor of choice.

[Check the project's GitHub repo](https://github.com/waseem-medhat/gopen) for the
source code, pre-built binaries, and any relevant documentation. The rest of
this article will be more of a blog-like walk-through with my thought process
and learnings from the project.

## Background

The idea of Gopen started as a potential dogfood solution to the relatively
straightforward problem of having to navigate to a project folder and open
Neovim every time I open a terminal. I went with the idea that if I had a
problem I wanted to solve, it's very likely someone else has the same problem
that Gopen would help with. So, I made sure my CLI is usable and
well-documented.

It started as a simple command-line tool where you write the appropriate
command and supply any necessary arguments in the shell. Then, I upgraded it
with an interactive TUI on top, including a search functionality to make it
easier to find aliases. This again came from a personal problem that I wanted
to solve, and that was that I used Gopen for a long time and added too many
aliases for me to remember, which lends itself well to interactive search.

## Technologies

The command-line part of Gopen is written entirely in Go and its standard
library. Go seems like a great tool for developing command-line utilities like
Gopen since it's simple to write, fast to run, and compiles to native OS
binaries for anyone to use without the need for the source code and an
interpreter.

To add the interactive TUI, I used the popular Go package [Bubble
Tea](https://github.com/charmbracelet/bubbletea). It has a relatively
straightforward framework for reactive programming to define the visual
components of the UI and the data upon which depends the rendering (and
re-rendering) of that UI.

Some small amount of automation was done with a makefile. The file simply
contains some commands for formatting, testing, linting, and compiling the
three binaries.

## GitHub & Collaboration

Because I thought the tool may be interesting for other people to use, I paid
as much attention as possible to the GitHub repo. I used the `README.md` to
provide clear documentation on how to install and use Gopen. Pre-compiled
binaries (for Linux, Windows, and MacOS) are also available in the
[releases](https://github.com/waseem-medhat/gopen/releases) page for direct
download and use.

I shared the repo in Discord servers to ask for feedback, and thankfully, it
got picked up by other users and got a few stars. One of them even gave me
excellent feedback and then collaborated with me on the project in both issues
and pull requests.

## Skills

As a portfolio project, Gopen demonstrates these skills with Go:

- CLI/TUI development
- Handling command-line arguments
- File I/O
- JSON marshaling/unmarshaling
- Go doc comments on functions and packages
- Testing with `go test`
- Linting with `golangci-lint`
- Cross-compiling for multiple operating systems
- Automation via makefiles
