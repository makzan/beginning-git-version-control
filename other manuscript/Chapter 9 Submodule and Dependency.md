# Chapter 9: Submodule and Dependency

By Makzan, version 1.0, First Draft. 2015-11-21.

## Git submodule

```
$ git submodule add <remote URL> <local path>
```

When changing sub-modules in local:

``` bash
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
  (commit or discard the untracked or modified content in submodules)

        modified:   vendors/super-js (modified content)
```



Otherwise, if the submodule changes externally.

We can go into the submodule folder and call `git pull`. Or if you want to update all, you can call the `git submodule foreach --recursive git pull`.


``` bash
$ git submodule foreach --recursive git pull
Entering 'vendors/cool-css'
remote: Counting objects: 5, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From /home/ubuntu/workspace/cool-css
   2b5252a..1c3d7a7  master     -> origin/master
Updating 2b5252a..1c3d7a7
Fast-forward
 cool.css | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
Entering 'vendors/super-js'
Already up-to-date.
```

After the pull, the changes hasn’t been marked into commit yet. When you git status, you see the vendors/cool.css is changed but not staged:

``` bash
$ git status
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   vendors/cool-css (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
```

This is because submodule is a dependency and you need to explicitly tell the git to really change the reference to the new HEAD of external source.

A simple git add and commit will mark that current project depends on the new HEAD.

If you don’t want the new change and you want to revert the dependency to the current commit, you can use `git submodule update`.

