# Chapter 4: Flow Control

There are different flow control approaches we can follow when using Git within a team.

## Git flow
There is a flow on switching branches. It’s an organization of branches that each branch indicates a meaning.

* Master
* Staging
* Development
* Deploy
* Hot fix
* Features

There is a branch dedicated to stable commits. Then there is a branch that contains latest working code, which is often “master”. There is a “development” branch which contains commits that may break.

Then for each new feature, we create a branch from the “development” branch. We may call it `fea_name` or `dev_name`.

For example, `dev_auth` or `dev_saving_record`.

Eventually, these feature branches are merged into the development branch. When the code passes the quality test, it will be pushed to staging branch for further testing. Finally, the code will be pushed to the deployment branch which will be built into production environment.



NOTE: In some git flow, the master is used as the stable branch. Then a development branch is created to represent the current developing code. On the other hands, some teams chose to make master the current developing branch. They create another branch, usually named “stable” or “deploy”, to represent the current stable code that is on production environment.

To make thing clear,  in my book, I will refer to the production ready branch as “deployment”, and the developing code branch as “development”. When I mention “master”, usually it is not related to the git flow.

## Hierarchy

We can setup hierarchy.

That controls people and how they access the repo. Also how they do  on each step of development.

For example, the development team

And the project manager manages

Then there is a QA team to perform quality testing

There is one man in charge of deploying the code to master.

## Hot fix branch
When the code in production has bug, we want to fix it based on the production code. This is almost the only case that we will make changes directly on the deployment branch.

In such case when a serious bug is found in the deployment branch. We check out the deployment branch and create a new branch. Usually we call the branch "hotfix".

Then we commit the changes on this hot fix branch and push back  to the deployment branch when we are done.

These changes are then pull back to the master/development branch. And team members may (or may not) merge the changes into their development branch. It depends if the changes affects the current developing features.

If the hot fix doesn't affect existing developing features, developers don't need to merge that changes. The code will merge in master/development branch when developer finished the feature branch and push to the master.

## Feature development branch

Development branch

Under this branch, we work on new features.

For each feature, we create a feature branch.

Each feature branch is responsible for a single feature.

Under each feature branch, we are freely to create sub branch as much s we like. These branches are treat as the experiments on specific feature.

For examples, given a feature requirement, there could be more than one way to solve the problem. And sometimes we don't know which one is better until we do some exploring. Creating branches allows us to explore the code into two, or several, very different directions, without each code conflicting with each other.


## Stable deployment branch

TODO: The stable deployment branch


## Git Merge with --no-ff

When we merge development branch into stable branch, we may choose to git merge with option `--no-ff`. This means even the stable branch can be fast forward, we still want a new commit to create. In such case, when we git log the graph, we can always see that that is a merge with 2 parents node.

In other branches, such as development and features branches, I still use normal merge or rebase.













