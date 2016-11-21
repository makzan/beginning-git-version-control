# Chapter 6: Conflicts

By Makzan, version 1.0, First Draft. 2015-11-21.


## How does conflict exist

Conflict exists when we try to merge 2 branches which edit the same line of source file.

Conflicts don’t happen when the merge is fast-forward. It may happen when the merge merges 2 different branches.

/27066DD2-CF64-40C8-9278-60A83354B468.png

## Resolve Conflicts

In this section, we take a look at resolving conflicts.

This section assumes that we are working on a web project with a very basic index.html file. We created 2 branches **index_a** and **index_b**. Both made changes on the `index.html` file.

Here is the git log output:

```
$ git log
* 94c2e8f - (index_b) Update copyright. 
* 3707797 - Update header.
| * fd581eb - (HEAD, index_a) Update index with 2015.
|/  
* 52aec20 - (master) 
```

When we try to merge index_b with index_a, it shows a conflict. When you `git log`, you won’t see the merge commit appears. This doesn’t mean the merge is aborted. It just mean the merge is paused and waiting us for further operations.

```
(index_a) $ git merge index_b
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
makzan@mz-main:~/workspace/git-samples/test2 (index_a|MERGING) $ 
```

When we `git status`, there is an “unmerged changes”.

```
Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:      index.html
```

Or in short form of status, there is a `UU`.

```
UU index.html
```

When you open the index.html in editor, you shoud see something like `<<<<`, `====` and `>>>>`.

Conflict example:

```
This is HTML Sample for my Git course.

Title: This is a sample.

<<<<<<< HEAD
Footer: Copyright 2015.
=======
Footer: Copyright 2016.
>>>>>>> index_b
```


If you just want to keep one version from either branch, you may use `--theirs` or `--ours`.

```
$ git checkout --ours index.html
$ git checkout --theirs index.html
```

If you want to get back the conflicted merge status, you can use the `--merge` option.

```
$ git checkout --merge index.html
```

After you manually clean up the file and get rid of all unwanted content, such as `<<<<`, `====`, `>>>>`, you can `git add` the conflicted file and commit the merge.

As the `git status` said, **git add <file>..." to mark resolution**, 


After we add all conflicted files and commit the merge as a commit, the merge operation is done.

Here is the `git log` after merging.

```
$ git log
*   40a0d08 - (HEAD, index_a) Merge with index_b
|\  
| * 94c2e8f - (index_b) Update copyright.
| * 3707797 - Update header. 
* | fd581eb - Update index with 2015. 
|/  
* 52aec20 - (master) 
```


Reference: [git checkout](http://git-scm.com/docs/git-checkout)






