### git Workflow

Below text is copied from:
https://www.openshift.com/wiki/github-workflow-for-submitting-pull-requests

##### Cloning your fork
Clone the repository from your fork:

```git
   git clone ssh://git@github.com/<username>/<reponame>.git
   git clone ssh://git@github.com/JamesClonk/martini.git
```

Add the upstream repository so that you can pull the latest changes:

```git
   git remote add upstream git@github.com:<original-username>/<original-reponame>.git
   git remote add upstream git@github.com:codegangsta/martini.git
```

##### Tracking an existing branch    
List all your branches:

```git
   git branch -a
```

To start tracking an already existing branch from origin locally, use the following commands:

```git
   git branch <branch> origin/<branch>
   git branch development origin/development
```

##### Working on a topic branch    
Always try to avoid working on the master branch. It usually results in merge conflicts and/or update issues. Instead, work on a bug/feature/topic branch whenever possible.

```git
   # start from the master branch
   git checkout master

   # create a new branch
   git branch dev/jamesclonk/new_feature/12345

   # switch to the new branch
   git checkout dev/jamesclonk/new_feature/12345

   # ...make changes...
```

##### Staying updated
Once a fork has been created, it does not automatically track the upstream repository. Follow the steps outlined below to keep the master branch up-to-date.

```git
   # pull the latest changes from upstream
   git fetch upstream
   git fetch upstream --tags

   # make sure there are no un-committed changes
   git stash

   # make sure we are working on the master branch
   git checkout master

   # merge the latest changes
   git merge upstream/master

   # push the updates changes to your GitHub fork
   git push origin master
   git push origin --tags

   # return to your bug/feature branch
   git checkout dev/jamesclonk/new_feature/12345

   # rebase this branch onto latest code from master (expect conflicts)
   git rebase master

   # ... resolve conflicts

   # push the rebased branch back to your fork
   git push origin dev/jamesclonk/new_feature/12345 -f

   # restore any un-committed changes
   git stash pop
```

**Note**: The git stash steps are optional. It is easier if you commit all changes before attempting a rebase.

##### Squashing your changes into one revision
Before you submit a pull request, rebase all your changes onto a single commit. This makes it easier to review and also makes reverting the code easier in case of any build breakages.

```git
   git rebase -i master
   # ... squash commits ...
```
