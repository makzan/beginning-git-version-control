# Chapter 2: Behind the Scheme

By Makzan, version 1.0, First Draft. 2015-11-21.

In this chapter, we learn how git works behind the scene. Specifically, we will learn:

- How git manage snapshots.
- How git manage branch pointers.
- The 3 stages of tracking changes.


## The .git folder

After git init the current folder, git creates a `.git` folder in the project directory.

The `.git` folder contains every thing git needs to maintain the repository. 

## The different stages of changes tracking

There are several stages for a file. 

They are: 

1. untracked files
2. tracked files with non-staged changes
3. tracked files with staged changes
4. committed changes

You can see the stages of the changes when you `git status` your project folder.


```
Your branch is up-to-date with ‘origin/master’.

Changes not staged for commit:
  (use “git add <file>...” to update what will be committed)
  (use “git checkout -- <file>...” to discard changes in working directory)

        modified:   app/controllers/folders_controller.rb
        modified:   app/views/folders/show.html.erb
        modified:   config/routes.rb

Untracked files:
  (use “git add <file>...” to include in what will be committed)

        app/views/folders/_public_list_document.html.erb
        app/views/folders/public_folder.html.erb

no changes added to commit (use “git add” and/or “git commit -a”)
```


### Untracked files:

The file is usually new and haven’t been tracked yet. 

NOTE: If you don’t want a specific file to be tracked. You should add it to `.gitignore` file. Don’t just leave that file there showing up every time when you view the `git status`. It’s because we want to make sure we can reach the state of clean working directory.

Here is how a clean git status looks like:


```
On branch master

nothing to commit, working directory clean
```



### Changed but un-staged:

The file is under tracked and there are changes since last commit. 

### Staged:

The changes is marked and will be added to repository in next commit. 

 [Reference of staging area](http://git-scm.com/about/staging-area) 

### Committed:

The changes are stored in the git repository. You can’t see it in `git status`. But you can view them by using `git log`. 

When we learn how to undo changes by using `git reset`, we will need the concept of these stages.


## Snapshots links

When we commit changes into a snapshot, git saves the diff. 

Each snapshot points to its parent. 

And there are pointers pointing to the last commit. 

So given any snapshot, we can trace the changes back to its root, first, snapshot. 

It given any snapshot, we can construct the files by applying the diff patches from its root snapshot. 

You can foresee from their mechanism that this design approach is good for source code and plain text files. It uses text patches to maintain the version changes.

But if we do version control with binary files, such as `.psd` format, it needs to store the file for each commit. 



