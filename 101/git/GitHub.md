#### Submitting a patch
Once your code is ready to be submitted, you will need to submit a pull request with your changes.

1. Update your branch and make sure you are rebased off the latest upstream/master
2. Squash your commits onto a single revision
3. Submit a pull request on GitHub 

---
#### Local GitHub PRs

GitHub provides a special pulls remote "namespace" for PRs on the upstream repo, so it can be added as a fetch pattern to .git/config:

```git
   [remote "upstream"]
      url = https://github.com/neovim/neovim.git
      fetch = +refs/heads/*:refs/remotes/upstream/*
      fetch = +refs/pull/*/head:refs/pull/upstream/*
```

After `git fetch --all`, ALL pull requests will be available in the local repo in the local pull/ namespace. To check out PR #42:

```git
   git checkout -b foo refs/pull/upstream/42
```
