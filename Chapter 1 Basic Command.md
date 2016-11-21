# Chapter 1: Basic Command

By Makzan, version 1.0.2, First Draft. 2016-11-21.

In this chapter, we will explore the fundamental things to get started using git version control. 

We will learn to:

- Install and init a git repository.
- Commit the changes as snapshot into the repository.
- Write helpful commit messages.
- View the current changes status.
- View the history log of the commit snapshots.

## Install and Config
This section covers the git program installation and configuration.

### Installation

John’s team has development machines running Windows and Mac. The servers are running Linux. To begin with git version control, the team install the git program in these operating systems.

In Windows, they use the installer because it handles everything we need to run git on Windows. It also include a GUI helper. In Mac, the git comes with Xcode—A development IDE for Mac. In some Mac that don’t have Xcode installed, they install the git program with the brew.

In their Linux server, the team uses the build in package manager, e.g. apt-get for Ubuntu, to install the git program. 

Now, assuming we are part of John’s team. We are going through the class to learn git version control to fit our development team’s code versioning requirement.

### Configuration

After installed the git program, we need to config it. At least, we need to set the username and email address so that we can know who is making changes on the code.

In command prompt, run the following command.

NOTE: This is my information, you may want to set yours.

Set up user name and email:

```
git config --global user.name "Thomas Seng Hin Mak"
git config --global user.email "mak@makzan.net"
```


This is the information that we can trace who has been working on what later when we need to collaborate the code with other members in the team.

NOTE: You can set project specific name and email by running the `git config` command without the `--global` option.

## Setting up filename for unicode

You can set Git to use unicode in filename by configuring the following:

```
git config --global core.quotepath false
```

## Init and First Commit
In the following steps, we will learn the very basic commands to control a project folder with git. Then we will make changes to the project files and save the snapshots into the git repository.

### Time for Action—Project initialization

1. Create a folder for our project. Let’s name it “Sample Project”.
2. Create some files inside the project folder. Optionally, put some dummy content in the files.
3. Run the `git init` command.


    ```
    git init
    ```
    
    
    The `git init` initials the current folder as a git controlled repository.

4. Run the `git add .` command to mark the files to be version controlled.

    ```
    git add .
    ```
    
    
    `git add` requires the input of files to be added. the `.` means adding all files in the current directory.

5. Run the following `git commit` command to commit the marked files into the repository. This is the step that really save the changes as a snapshot.


    ```
    git commit -m “First commit.”
    ```


NOTE: As a beginner, it’s easy to forget the commit message. `git commit` requires the message exists, but sometimes beginners simply avoid it by using `-m “”`.

### Further steps
We have learnt the `add` and `commit` command. By using these commands, now you can make changes on your files/source code. When you feel that needs a snapshot, you can `git add` the changed files and `git commit` them into the version-controlled repository.


NOTE: You can combine the `add` and `commit` into one command: `git commit -am ‘<MESSAGE>’`. It adds all the changes into commit. Use it carefully.

## Writing git commit message

There are some points that we need to know about writing git commit messages. 

1. Use present tense. 
2. Begins with a verb. Just omit the subject because it is always “I”, the developer. 
3. Use the first line as summary. 
4. For a long message, use the text editor instead of the one line option `-m`. For a long message, add two line breaks and write the detail after the first summary line. 

It’s not required to mention file names in message. The file changes can be viewed in the log. No need to mention the file unless you need to refer to the file in your message. 


## Current Changes Status

We can observe the current status by using the `git status` command. 

For example, when we run the `git status` command in a directory with changes, we will see he following result. 


```
On branch master
Your branch is up-to-date with ‘origin/master’.

Changes not staged for commit:
  (use “git add <file>...” to update what will be committed)
  (use “git checkout -- <file>...” to discard changes in working directory)

        modified:   app/assets/javascripts/application.js
        modified:   app/views/documents/_form.html.erb
        modified:   app/views/documents/show.html.erb

Untracked files:
  (use “git add <file>...” to include in what will be committed)

        app/assets/javascripts/components/last-save.js.jsx
        vendor/assets/javascripts/moment.js
```


For the status, you may observe that there are two stages of files: (Actually there are three, we will go through it later)

1. Un-staged file changes, in red color. 
2. Staged file changes, in green color. 

The third stage is `committed` file changes, which is stored as a snapshot in the git repository and hidden in the `git status` command. 

**Help message**

In the git status, there are helping messages that guides you the next actions you can perform on those changes. 

For example, it tells you that you can use add to stage the changes. And you can use checkout to un-stage the changes.

**Short version**

There is a short version of the status. If you are really familiar with the status output and what you can do with those changes, you can turn off all the unnecessary output by using the option `--short`, or `-s`.

`TODO`: make sure the options are correct. 


## Commit log

The log shows the history of the commit snapshots. 

There are several log options. The default one isn’t such useful actually. 

I usually view my log with the following options. 


```
$ git log --oneline  --graph --decorate --color --all
```


It’s a very long command, right? So I usually set it as an alias command. This can be done by setting the alias in the `.gitconfig` file. 


```
[alias]
  lg = log --all --oneline --graph --decorate --color
```


NOTE: The `.gitconfig` file is usually in the home directory.

Please refer to “Git Alias Configurations€” for git command alias.

### Explaining

So what does those options mean?

The `--oneline` shows the simplified version. 

The `--graph` shows the commit relationship path on the left. So that the sequence of log becomes a commit path. 

The `--all` shows all branches, including the remote branch. Otherwise, `git log` only shows the current branch. 

The `--decorate` shows the branch pointers to the commits. 

The `--color`, as the name suggests, makes the log output colorful and easier to read. 


## Migrate from SVN

John’s team uses SVN to control their code before moving to Git.

If you have version control experience with SVN, here is what’s similar and what’s difference. 

**Workflow**

At the beginning of learning git, you may follow the workflow of SVN. In the morning, you check out the code from the centralized repository. You work on your code. During lunch break or get off the work at evening, you check in the code and merge your changes into the centralized repository.

When you follow this SVN approach, you don’t get much benefits of using git. Git’s power comes from it’s distributed local repository. But it’s a good starting point to get familiar with the git command.

### The similar

In collaboration, you need to push your code to a centralized server. Others pull and merged your code. 

### The difference

The repository is stored locally. The remote one is a duplicated one. Every local repository is a full working copy.


### Technically

The merge is done in local instead of in the server. 

Branch is essentially a pointer. Creating a new branch on a current state only creates a new pointer. In SVN, it copies a new folder and files to create branch. 


### Benefit of storing repository locally

- You can work offline. You may be on train, on flight, on trip with no internet access. You’re disconnected and this is the best time of working. So you can continue on your code. Make changes and commits local. Exploring and experimenting freely.
- Super fast response. Git encourages developers to create branches and experiment with code, because every changes are tracked. This confidence come from it’s fast response when creating and switching branches. This is because these repository operations are done locally. And because its mechanism optimists on branch switching.
- Review before push. Git encourages creating branches and committing without worrying about losing the code. There are chances that the commits tree and branches become messy and complicated. Since all those commits are local only until we push those commits to a remote branch, we can re-organizing them before push them to remote.















