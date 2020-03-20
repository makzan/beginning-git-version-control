# Introduction

In this book, we will go through the basic concept of Git version control.

I design this book as a journey of the main character name John. He is an IT manager that manage a team of developers. He is also in charge of deploying the code to the production server.

## Why this git book?

Git is getting more and more powerful. It means more and more commands for us to control every little detail of code changes. That’s good. But as a new learner, I trim the content to provide only the essential concepts and the best practices.

For example, I recommend `git fetch` + `git merge` always instead of `git pull`. You’ll learn all these commands in elsewhere, but in this book, I tell the _why_ and their pros and cons. (In chapter 5)

## About Author

I am Thomas Seng Hin Mak, but you may find me on Internet as “Makzan”.

I have been using git version control since 2009. Before moving to git, I used SVN in a game development team. I changed to use git personally and then encouraged the whole team to move to git. Afterwards, I tried different git version control flow in different team, including HTML5 games development, book writing, iOS app development and web projects. I also used different remote repository approaches, such as GitHub, Bitbucket, self-hosted git and Dropbox sync.

## Book Status

The book is in first draft stage. That means content is raw and in-edit.

I follow the lean publishing philosophy. We make the book published as soon as it is written. Then we update the book periodically.

You will also find the version status in each chapter.

## Version history:

- 2015-11-23: First draft
- 2015-12-07: Working on the remote content.
- 2015-12-28: Write more about merge, rebase, cherry-pick and submodule.
- 2016-11-07: Organize content into HTML format.
- 2016-11-20: Minor fixes and PDF output.
- 2016-11-21: Add config of quote path.
- 2017-06-30: Moved the manuscript to Ulysses and setup Leanpub. Added “Why this book” section.

# Book reference
This short book provides only the essential techniques to help you get started using git version control. It’s a tips and tricks sharing from my 8 years of experience.

If you need to reference certain concepts of commands, I recommend reading the [Pro Git] book, or its web format on [git-scm.com].

That is the go-to book to learn git. You can also find the reference of git commands on  [git-scm.com/docs].

Besides the Pro Git book and the official reference, there are some other online resources:

- [Git Ready]
- [Git Pretty]


# Beginning of the story
This book is a journey of how the imaginary project manager—John—manages his IT development project with Git version control.

Meet John. He is an IT manager who manages a team of developers. This is a software company that builds web application. They need to manage production servers that serves their code. They also have a staging server for internal testing. Within the team, several developers work together with local development machine.

They have been using SVN for their version control. Now they want to migrate to use Git version control.

This is a short journey about how John’s team learn to manage their source code with git version control.


## Why Git?

Here are some advantages of Git version control.

- Git is fast.
- Git is local hosted.
- Git repository is distributed.