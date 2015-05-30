#### Forking big go project with nasty dependencies

* First clone it locally int $GOPATH/src/github/<big>/.

```git
   git clone https://github.com/big/project.git
```

* You now have a `$GOPATH/src/github.com/big/project` directory, which is actually a git repository.
* Fork big project on GitHub, and copy the SSH URL shown for your fork into clipboard.
* Go into `$GOPATH/src/github.com/big/project` and type:

```git
   git remote add fork git@github.com:JamesClonk/project.git
```

* Make code changes, compile and test them, then:

```git
   git push fork
```

* Then you can open a pull request to get your code merged into the main repository.
* To keep your fork in sync with the original repository, you essentially need to do:

```git
   git pull --rebase origin
   git push fork
```

* Before creating pull requests its probably best to rebase to clean your commit history.
