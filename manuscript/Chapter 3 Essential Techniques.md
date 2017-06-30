# Chapter 3: Essential Techniques

By Makzan, version 1.0, First Draft. 2015-11-21.

We have learned the basic commands to keep adding changes as snapshots. It’s time to learn more techniques.

## Git add interactive

`git add` comes with an interaction mode.

```
$ git add -i
           staged     unstaged path
  1:    unchanged        +2/-2 index.html

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help

What now> 2
           staged     unstaged path
  1:    unchanged        +2/-2 index.html
Update>> 1
           staged     unstaged path
* 1:    unchanged        +2/-2 index.html
Update>> 
updated one path

What now> 1
           staged     unstaged path
  1:        +2/-2      nothing index.html

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
```


You can use the command to add file by choosing their index number.

You can also use `patch` to add line by line inside a file.

```
Stage this hunk [y,n,q,a,d,/,s,e,?]? ?
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk nor any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk nor any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help
```


For example:

```
What now> s
           staged     unstaged path
  1:    unchanged        +2/-2 index.html

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> p
           staged     unstaged path
  1:    unchanged        +2/-2 index.html
Patch update>> 1
           staged     unstaged path
* 1:    unchanged        +2/-2 index.html
Patch update>> 
diff --git a/index.html b/index.html
index 5ba3e85..df49622 100644
--- a/index.html
+++ b/index.html
@@ -1,5 +1,5 @@
-This is HTML Sample.
+This is HTML Sample for my Git course.
 
 Title: This is a sample.
 
-Footer: Copyright.
\ No newline at end of file
+Footer: Copyright 2016.
\ No newline at end of file
Stage this hunk [y,n,q,a,d,/,s,e,?]? ?
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk nor any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk nor any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help
@@ -1,5 +1,5 @@
-This is HTML Sample.
+This is HTML Sample for my Git course.
 
 Title: This is a sample.
 
-Footer: Copyright.
\ No newline at end of file
+Footer: Copyright 2016.
\ No newline at end of file
Stage this hunk [y,n,q,a,d,/,s,e,?]? s
Split into 2 hunks.
@@ -1,4 +1,4 @@
-This is HTML Sample.
+This is HTML Sample for my Git course.
 
 Title: This is a sample.
 
Stage this hunk [y,n,q,a,d,/,j,J,g,e,?]? y
@@ -2,4 +2,6 @@
 
 Title: This is a sample.
 
-Footer: Copyright.
\ No newline at end of file
+Footer: Copyright 2016.
\ No newline at end of file
Stage this hunk [y,n,q,a,d,/,K,g,e,?]? d

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> s
           staged     unstaged path
  1:        +1/-1        +1/-1 index.html

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> q
Bye.
$ git st
On branch index_b
Changes to be committed:
  (use “git reset HEAD <file>...” to unstage)

        modified:   index.html

Changes not staged for commit:
  (use “git add <file>...” to update what will be committed)
  (use “git checkout -- <file>...” to discard changes in working directory)

        modified:   index.html

$ git diff --cached
diff --git a/index.html b/index.html
index 5ba3e85..68b050a 100644
--- a/index.html
+++ b/index.html
@@ -1,4 +1,4 @@
-This is HTML Sample.
+This is HTML Sample for my Git course.
 
 Title: This is a sample.
 
$ git diff
diff --git a/index.html b/index.html
index 68b050a..df49622 100644
--- a/index.html
+++ b/index.html
@@ -2,4 +2,4 @@ This is HTML Sample for my Git course.
 
 Title: This is a sample.
 
-Footer: Copyright.
\ No newline at end of file
+Footer: Copyright 2016.
\ No newline at end of file
```

## Check out specific commit

We can check out specific commit by using the following command.

```
git checkout <commit hash>
```

The commit hash is a 40 characters length of alphanumeric. We don't necessarily need to write the all 40 characters. Just include the first few characters to allow git to identify that commit. For example: `git checkout 123456` would be enough most of the time to identify a unique commit. 

When you checkout certain commit. You’ll notice two things:

1. The git checkout command prints a large paragraph of text. It is to warn you that you have checked out a branch without any pointers. That means that is a detached branch without any branch name. We usually checkout and work on branch instead of directly referring to commit hash. 
2. The files in the working directory changes to the state of that commit. Don’t worry, our commits are safe and we can checkout our latest code by doing `git checkout master`.

Read the "branch" and "git flow" section for more about using branches. 

## Creating branch

We can create branch by using `git checkout -b`.

For example, the following command creates a new feature branch.


```
git checkout new_feature
```


This creates a new branch. But actually nothing really changes here until we create new commits. When you git log the commits, you still see the same commits graph. The only difference is now there is a new_feature brands name appears at where the HEAD at. 

We will see how branch works when we make changes and commit it. Afterwards, the git log shows commit graph that contains the new_feature and the master, which points to two different commits. This is because we created a branch from where master pointed at and then move forward with new commits. 

To make things more interesting, now we go back to where master points at. To go back, we `git chrckout master`.

Now we make some other changes on master and commit it. When we git log to see the commit graph, we see two commits are diverse into two direction, both from the same parent commit but now one is master and the other is `new_feature`. The HEAD points to the current commit. When we `git checkout new_feature` again, we can see the HEAD now points to new_feature. 

## git merge

After we created different branches, we need `git merge` to merge the current branch into the other branch.


```
(master branch)$ git merge feature_a
```


It’s result is a recursive merge. That happens when we merge 2 branches that has a different commits history.


/05A54CFB-1015-4255-A152-E039DC502658.png

Afterwards, we may checkout the `feature_a` branch and merge to `master`.


```
$ git checkout feature_a
$ git merge master
```


It’s result is a fast-forward merge. That happens when we merge branches that is in the same timeline.

## Git diff


Diff between un-staged changes and staged / commuted changes: 

```
git diff
```


This compares the current non-added changes with the last commit in the current branch.


```
git diff --cached
```


`--cached` compare the staged changes (added but not committed) with the  last commit in the current branch.


```
git diff branchA branchB
```



Why need to diff before committing?

We want to check what’s the changes between the latest code and the last committed code. 

Assume the following `git status` result. We see that there are two files changes. One file is `last-save.js.jsx` and the other one is `app.css.scss`.

An example of git status with two changes files:

```
$ git status
On branch master

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   app/assets/javascripts/components/last-save.js.jsx
        modified:   app/assets/stylesheets/app.css.scss

no changes added to commit (use "git add" and/or "git commit -a")
```


Then, we use the `git diff` to check the code changes before committing them into the repository.

In the diff, we find that the 2 files are actually 2 different things. One file is a React JS view component and the other is a CSS styling improvement. We didn’t commit before making changes to another feature.

We add 1 file and commit it, then we commit another file.

And result in two different commits for two different purposes. 

## Maintaining a clean commit history

Before we commit, we may want to clean the commit to make it containing only what’s relevant. 

So each commit should make changes on only one thing. 

For example, it is a good habit to check the changes difference with `git diff`. 

## Daily Workflow
Every day, here is the workflow. 

1. Fetch to see if there is any new updates from your team mates.
2. If the team mates has updated code in your working branch, merge that branch with priority.
3. Check what's the work in progress branch.
4. Check out the working branch and start writing the code.
5. When there is enough changes made, commit the changes to make a snapshot. 

## Git Alias Configuration

We can set alias in the `.gitconfig` file.

```
[alias]
    st = status
    lg = log --all --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%C(bold blue)<%an>%Creset' --abbrev-commit
    ll = log --all --oneline --graph --decorate --color
```

NOTE: Most likely the `.gitconfig` file is in current user’s home directory.

## Ignoring files with .gitignore

the `.gitignore` file allows us to list files that we don’t want to track at all. These files won’t appear as “Untracked files” when viewing the `git status` result.

You can ignore an entire folder by specifying the folder name. Or you can ignore certain type of files with the wildcard character. For example: `build/*.exe`.

We usually want to ignore the build and output because these can be compiled. In version control, we control the source code.

NOTE: You can still force adding files that is ignored by using the `git add -f` option.

## Git tracks files, not folder

Git doesn’t track folder.

If we need to track folder, we usually add a hidden file there. Community often use an empty `.gitkeep` file for this purpose. But it’s not a standard.






