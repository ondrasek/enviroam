# Manage your .dotfiles with a simple tool
Storing and managing your dotfiles in GitHub repository seems to be a good idea.

* GitHub has adopted this practice for GitHub Codespaces
* There are popular dotfiles collections hosted on GitHub, such as:
  https://github.com/thoughtbot/dotfiles or https://dotfiles.github.io

I have been using a dotfiles repository hosted on GitHub for years, adding configuration files for
Linux, Windows and MacOS hosts. This gives me backup, versioning and I can also move between hosts
effortlessly.

Nevertheless, it is still a manual process, so I have decided to automate.

Dotfiles are just files, so managing them in git repository is easy. What's cumbersome is copying
the files from their well-known location (such as `~/.config`) to the git repository and back or
maintaining the symlinks manually.

You can simply turn your home directory into a git repository, but that will give you a lot of
clutter and you are one `git add *` from total mess.

The purpose of this tool:

* Maintain dotfiles as symlinks into your local working copy.
* Make it easy to use single/multiple repositories with your dotfiles.

## Scenarios

* I have one operating system, one host and I just like to backup and version my dotfiles.
* I have multiple hosts/multiple operating systems and I want to put everything into one git repo,
  maintaining simple folder structure.
* I have multiple hosts/multiple operating systems/multiple host "flavors". I need compatibility
  with tools like GitHub Codespaces

## Prerequisites

`dotfiles-tool` relies on:

* Your git tooling setup is working and git binary is in your `PATH`.

## What's included?

* `dotfiles-tool` CLI utility for working with dotfiles.

## What `dotfiles-tool` is not?

The tool does neither replace nor encapsulate git. You still can and should use git to commit your
changes in your dotfiles.
