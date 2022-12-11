# Manage your dotfiles with a simple tool
Storing and managing your dotfiles in a git repository seems to be a good idea.

* GitHub has adopted this practice for GitHub Codespaces
* There are popular dotfiles collections hosted on GitHub, such as:
  https://github.com/thoughtbot/dotfiles or https://dotfiles.github.io

I have been using a dotfiles repository hosted on GitHub for years, adding
configuration files for Linux, Windows and MacOS hosts. This gives me backup,
versioning and I can also move between hosts effortlessly.

The purpose of this tool:

* Maintain dotfiles as symlinks into your local working copy.
* Make it easy to use single/multiple repositories with your dotfiles.

## Scenarios

* I have one operating system, one host and I just like to backup and version my
  dotfiles.
* I have multiple hosts/multiple operating systems and I want to put everything
  into one git repo, maintaining simple folder structure.
* I have multiple hosts/multiple operating systems/multiple host "flavors". I
  need compatibility with tools like GitHub Codespaces

## Why Bother?
Numerous dotfile tools exist already, just look at: [dotfile-manager · GitHub
Topics](https://github.com/topics/dotfile-manager). 

The most popular tool seems to be: [twpayne/chezmoi
(github.com)](https://github.com/twpayne/chezmoi) written in Go. There is one
written in Rust: [dotter (github.com)](https://github.com/SuperCuber/dotter). 

My main reason to create another tool is to learn Rust. At the same time, I have
additional [[#Goals]] for the tool.

Meet `enviroam` a tool to setup and maintain user profiles and configuration
files among multiple machines and environments, such as Windows boxes, CI/CD
containers, GitHub Codespaces, Linux machines, WSL instances, etc.

## Goals
1. The `dotfiles` repositories can be completely clean. There is no
tool-specific state information, just the dotfiles. It may make sense to keep
some additional config in the repo for specific cases, such as handling multiple
different platforms.
2. The tool shall support using more than one repository and merge dotfiles
intelligently. Such as one repo as generic, another one for platform-specific,
etc.
3. The tool shall support more than files - for example registry entries or
MacOS configuration entries (using `defaults`).
4. The tool shall allow the user to provide their own *source* and *local
working copy* of dotfiles, but also automate everything using git if desired.
5. The tool shall provide different plugins to *collect* various dotfiles and
configuration files, not only those present in the `$HOME` directory. Such as
the `WSL` configuration file, `$AppData`, files in the user profile, etc.
6. The tool shall provide different plugins or configuration to only *onboard*
parts of the configuration files, specifically skipping secrets or storing
secrets in secure way (i.e. fill in local/secret information when the file is
downloaded locally).
7. The tool shall support updating dotfiles when they are modified locally -
either automatically (potentially overwriting changes) or selectively, as
defined by the user.
