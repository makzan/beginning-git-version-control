# Introduction

In this book, we will go through the basic concept of Git version control.

I design this book as a journey of the main character name John. He is an IT manager that manage a team of developers. He is also in charge of deploying the code to the production server. 

## About Author

I am Thomas Seng Hin Mak, but you may find me on Internet as “Makzan”.

I have been using git version control since 2009. Before moving to git, I used SVN in a game development team. I changed to use git personally and then encouraged the whole team to move to git. Afterwards, I tried different git version control flow in different team, including HTML5 games development, book writing, iOS app development and web projects. I also used different remote repository approaches, such as GitHub, Bitbucket, self-hosted git and Dropbox sync. 

## Book Status

The book is in first draft stage. That means content is raw and in-edit. 

I follow the lean publishing philosophy. We make the book published as soon as it is written. Then we update the book periodically.

You will also find the version status in each chapter. 

/Version History.md


# Book reference
This short book provides only the essential techniques to help you get started using git version control. It’s a tips and tricks sharing from my 6 years experience. 

If you need to reference certain concepts of commands, I recommend reading the  [Pro Git](https://progit.org/)  book, or its web format on  [git-scm.com](http://git-scm.com/) .

This is the go-to book to learn git. You can also find the reference of git commands on  [git-scm.com/docs](http://git-scm.com/docs).

Besides the Pro Git book and the official reference, there are some other online resources:

- [Git Ready](http://gitready.com/) 
- [Git Pretty](http://justinhileman.info/article/git-pretty/) 


# Beginning of the story
This book is a journey of how the imaginary project manager—John—manages his IT development project with Git version control.

Meet John. He is an IT manager who manages a team of developers. This is a software company that builds web application. They need to manage production servers that serves their code. They also have a staging server for internal testing. Within the team, several developers work together with local development machine. 

They have been using SVN for their version control. Now they want to migrate to use Git version control. 

This is a short journey about how John’s team learn to manage their source code with git version control. 


## Why Git?

Here are some advantages of Git version control.

- Git is fast. 
- Git is local hosted.
- Git repository is distributed.