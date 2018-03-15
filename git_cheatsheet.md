
Basic Comands
======

Clone
------
* Download the code from link (`link`)
```shell
git clone link
```

Remotes
---------
* Add someone else's repository (`link_someone`)
```shell
git remote add someone link_someone
git fetch someone
```

* Don't forget to fetch

Fetch
------
* Download things (changes/branches) in someone's repo (`reponame`)
```shell
git fetch reponame
```

* If you omit `reponame`, then it uses `origin` by default

* If you don't fetch, you do not have access to any uploaded commits (since the last fetch)

* **Always fetch**

Branch
-------
* Do not start implementing new features onto your master (especially if you aren't comfortable with 
  rebase/merge/cherrypick)

* Check which branch you are on with
```shell
git status
```
or
```shell
git branch
```

* Branch off from the commit (e.g. `scrummaster/master`) that you would like to be your reference
```shell
git branch my_feature scrummaster/master
git checkout my_feature
```
or
```shell
git checkout scrummaster/master
git branch my_feature
git checkout my_feature
```
or
```shell
git checkout scrummaster/master
git checkout -b my_feature
```

* If you're not comfortable with rebasing/merging, try not to branch off of a feature branch that 
  has not been accepted yet. Since it's not accepted, it will probably require changes, which may 
  require tricky rebase/merge later on.
  
* Even if there is strong dependency between these two branches (e.g. function from one of the 
  feature branch is needed), it is better to branch off of the repo master. This way, we will end up
  with many small pull requests, rather than one giant pull request with all the dependencies. 
  However, it does make it harder to unit test. You would need to rebase onto the dependent branches
  before your code does not crash. You can copy over files as untracked changes. You can also bug
  your repo master to merge your pull request.

Commit
-------
* Save changes you made (to file `filename`)
```shell
git add filename
git commit
```

* Modify your last commit (e.g. forgot to add changes to file `filename`, change commit message)
```shell
git add filename
git commit --amend
```

* Commit for someone else. You can find their name from `git log`.
```shell
git add filename
git commit --author='Full Name <email address>'
```

Rebase
-------
* Apply changes in a branch (e.g. `master`) in someone's repository (`someone`) to your own branch 
(e.g. `feature`)
```shell
git rebase someone/master feature
```
* Note that your changes `feature` come after the reference `someone/master`
* Rebase interactively to drop, edit, reorder, or squash commits
```shell

git rebase -i someone/master feature
```

* Interactive rebase is an easy way to clean up your commits before a pull request. For example, if
  you have many commits like `fix travis errors`, `fix more travis errors`, `fix more errors`, then
  you can squash all those commits together into a single commit.

FAQ
====
