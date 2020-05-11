---
published: false
title: 'Learning about git!'
cover_image: 'https://raw.githubusercontent.com/ramclen/documenting-dev/master/blog-posts/Learning-about-git/assets/cover-image.jpg'
description: 'Learning basics about git'
tags: git, beginners, productivity
series:
canonical_url:
---

In this post, I will try to give you some concepts to help you to start learning about git. Git is known by almost all programmers or even all of them. It manages all the changes made to your files and projects in an easy way.

I love to see git like a save state on a video game, if I fail in next boss I will restart from my previous state and I will give another try with a different strategy.

So let us begin!

## What is git?

Git is a Version Control System. It means that git is going to help you to store and manage all the changes that you make to your file or project through the time. To do this, git works with repositories, and you have to commit those changes. Git runs on your local machine so you don’t need to have an internet connection.

## How to start using git

First of all, you need to install Git on your local computer. You can download it from [its website.](https://git-scm.com/)
When you have already installed Git, you have to get into your Project folder

```sh
  cd projectFolder
```

or you can create an empty directory for your project using

```sh
  mkdir projectFolder
```

and then, run the command

```sh
  git init
```

This command will initialize a Git repository in this directory.

## What is a repository?

A repository contains all the history of changes. It contains all the files managed by git. There are three principal local states related to files managed by git:

- Working directory
- Staging area
- Git repository

Working directory is the directory in our computer which holds all our application files and folders.
Git repository contains all the changes that we save in git, that are finalized and uploaded by a commit.
The staging area is in between, is a holding area, a kind of queue when we are waiting for the changes for the next commit.

## So, how can I add the changes that I’ve made to the staging area?

Simply, using the next command.

```sh
  git add myFile.txt
```

You can use this command followed by the name of the file that you want to add to this area or you can use a folder path that allows us to add all the files at the same time. This is

```sh
  git add .
```

We haven't committed our changes yet. In this area, you can move the files in and out without modify the git repository and review all the changes you have made before committing.

## Committing changes

Once we have our files in the staging area we can save them in our git repo. We'll have to use another command:

```sh
  git commit -m "Commit message"
```

When we make a commit, we are going to save the changes in all files that were in the staging area.
Commit messages are messages that we add to our commits to describe which kind of changes you have done. These messages have to be simples.

## How could I know the state of my repository?

Using the next command

```sh
  git status
```

Shows the status in both the working directory and staging area. It helps us to see in which state are the files you have modified so we can handle them.

## Can I see all the commits I have made?

Yes! There is a command that outputs the history of changes. We have to use:

```sh
  git log
```

This returns to us very important information about our commit history, like the ID of the commits, the author, the date and where is the head.
It maybe looks a little confusing if you have multiples commits, but there are a few options that you can use to have a better vision of this log. My favorite one is:

```sh
  git log --all --decorate --oneline --graph
```

This one, in particular, draws a graphical representation in one line and it's very visual. Try it yourself!

# Found a typo?

If you've found a typo, a sentence that could be improved or anything else that should be updated on this blog post, you can access it through a git repository and make a pull request. Instead of posting a comment, please go directly to [my github repository](https://github.com/ramclen/documenting-dev) and open a new pull request with your changes.
