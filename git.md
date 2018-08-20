---
title: Working With Git
created_at: 2013-11-25 20:16:20 +0400
kind: cheatsheet
keywords: [cheatsheet, code]
---

# GIT DVCS

## Config

```bash
$ git config --global user.name "Attila Malarik"
$ git config --global user.email "attila.malarik@gmail.com"
$ git config --global color.ui true
```

## New Repo

```bash
$ git init # create local repo in .git
```

### these steps come usually after init

```bash
$ git add .
$ git commit -m "Initial commit"
```

## Status

- check status often
- shows what's in the staging area (in need of committing)

```bash
$ git status
```

## Staging - Add stuff

- add files to the staging area for committing
- wildcards are permitted (e.g. *.txt)
- double quotes around wildcard looks for it in the whole project

```bash
$ git add <path>
$ git add --all
$ git add *.txt
```

## Unstage stuff - Remove (before commit)

```bash
$ git reset <path>
$ git reset HEAD <path>
$ git reset --soft HEAD^ # rollback last commit (^ - before, can be stacked)
$ git reset --hard HEAD^^ # undo last 2 commits and all changes
```

## Committing

```bash
$ git commit -m "Message"
$ git commit -a -m "msg" # stage & commit (only already tracked files!)
$ git commit -amend -m "msg" # add to last commit
$ git commit -am "msg" # add and commit
```

## Log

```bash
$ git log
$ git log --oneline --since="one week ago" --pretty=format:"%C(yellow)%h%Creset %s %C(green)<%an>%Creset"
```

## Rename

```bash
$ git mv foo.txt bar.txt
$ git commit -am "Renamed foo"
```

## Remove / delete

```bash
$ git rm <path>
```

## Remote servers

- no access control, either uses hosted services (like GitHub, BitBucket), or self managed solution (like Gitosis, Gitorious)
- "origin" is the de facto standard name for "canonical" repos

```bash
$ git remote add origin https://github.com/<username>/sample_app.git
$ git remote -v # show remote repos
$ git remote rm <name>
```

## Push content to remote repo

- do it every time you finish working locally!
- setup password caching on github: https://help.github.com/articles/set-up-git
- don't change history after push! (don't use reset, or commit --amend)

```bash
$ git push -u origin master # push current master branch to origin (-u sets destination as default)
$ git push # to default remote
```

## Pull content from remote repo

```bash
$ git pull origin master
```

## diff

```bash
$ git diff HEAD <filename> # filename is optional
$ git diff --staged # search through staged files too!
```

## Checkout

- checkout is a multi talent, it can switch branches, roll back, etc
- it is good practice to work on features in topic branches instead of the master branch

```bash
$ git checkout <branchname> # switch to a branch
$ git checkout -b <branchname>
$ git checkout -- octocat.txt # rollback until last change of octocat.txt
```

## branching

```bash
$ git branch # show current branch
$ git branch <branchname>
$ git branch -d <branchname> # delete a branch
```

## Forking on GitHub

### Add original repo as upstream

git remote add upstream /url/to/original/repo
git fetch upstream
git checkout master

### merge upstream to fork

git merge upstream/master

### Reverting all changes in fork to upstream's content

git reset --hard upstream/master  
git push origin master --force 

## LFS - Large File Storage

- https://git-lfs.github.com/
- tell LFS what file types to track in the repo (stored in .gitattributes), everything else is automatic

```bash
$ git lfs track "*.zip"
```
