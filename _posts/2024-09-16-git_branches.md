---
layout: post
title: Working with git branches
---

[Resource](https://learngitbranching.js.org/) used today

## git commit

git records a snapshot of all the tracked files in your directory

git wants to keep commits as lightweight as possible, so it can compress a commit as a set of changes, "delta" from one

git also maintains a history of which commits were made when. ancestor commits

```bash
git commit -m "your commit message"


```

## git branches

branches in git are lightweight. they serve as pointers to a specific commit

there is no storage memory overhead with making many branches

```bash
git checkout -b yourbranchname
git branch yourbranchname
git checkout yourbranchname
```

## git rebase

```bash
git rebase
```

## HEAD

symbolic name for the currently checked out commit (what commit you're working on top of)

HEAD always points to the most recent commit which is reflected in the working tree. Most git commands which make changes will strt by changing head.

normally HEAD points to a branch name. When you commit, the status of branch is altered and you can see this through HEAD.

### Detaching HEAD

meaning attaching it to a commit instead of a branch, don't really understand the explanation in the resourcet though on how to detach HEAD

```bash
git checkout HEAD^
```

## Relative refs

specifying commit hashes can be tedious but you can enter just enough characters until it could identify the commit you're refering to

relative commit:

moving upwards one commit at a time with ^
moving upwards a number of times with ~\<num>
you can ref HEAD as a relative ref

caret ^

```bash
git check out main^ 
# moves to the commit one step before the branch
main^^
# moves to the commit two step befor the branch
```

## The ~ operator

you can use the tolde(~) operator to move several step back in the commit tree.

```bash
git checkout HEAD~4
```

## Branch forcing

```bash
git branch -f main HEAD~3
# moves the main branch to three parents commit behind HEAD

git branch -f main c6
# moves the branch to the commit
```

Note: git branch -f command is not allowed for you current branch in a real git environment

reversing changes in git
there are many ways to reverse changes in Git.

reversing changes are similar to committing, it has both a low-level component(staging individual changes) and a high-level component (the changes that are actually reversed.)

```bash
git reset
# reverses changes by moving branch reference backwards in time to an older commit

git revert
# git reset does not work for remote branches, so to be able to reverse and share those changes, git revert is used

```

pushed (remote branch)
local (local branch)

## Git cherry-pick

```bash
git cherry-pick <commit1> <commit2> <...>
# copy a series of commit below your current HEAD
```

## git interactive rebase

when you don't know which commit you want to use for cherry pick, you can use:

```bash
git rebase -i HEAD~4
```

## Locally stacked commits

## Juggling commits

## Git Tags

a more permant mark of important points in your project history rather than using branches
you can reference this tag similarly to branch

```bash
git tag v1 "commit1"
```

## Git Describe

a command to describe where you are in relation to the closest tag

```bash
git describe <ref>
# if you don't specify a ref, git uses where HEAD is at
```

outcome will be \<tag>_\<numCommits>_g\<hash>

> tag: closest ancestor tag in history
> numCommits is how many commits away that tag is
> \<hash> is the hash of the commit being described 