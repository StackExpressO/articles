---
layout: default
title: Git workflow for developers
nav_order: 3
description: This workflow is for developers making contributions for CI/CD enabled repository
permalink: /vcs-scm/git-workflow-for-developers
---

# Get Started
{: .fs-9 }

## Overview

This workflow is created by following the strategy when 'Master branch is always production deployable'

So the master branch has always the changes ready for production.

## Get code on dev machine and do basic configurations

- Clone the repository to dev machine

```bash
git clone <repo_address>
```

- Set your name globally for git

```bash
git config --global user.name '<your name>'
```

- Set you email globally for git

```bash
git config --global user.email '<your email>'
```

## Start working on a new feature

- Checkout to master branch

```bash
git checkout master
```

- Update code from master

```bash
git pull origin master
```

- Create a new branch from master (Make the branch name relevant to feature and fix we are working)

```bash
git checkout -b <new_feature_branch_name>
```

- Make local changes, Modify the files which you want to. Test code on dev machine (Do your coding and all)

- Add files to git, after the files have been tested well on dev machine

```bash
git add <file1> <file2> <file3> ...
```

- Commit changes to local

```bash
git commit -m '<commit message>'
```

- Update master branch of the repo with latest remote changes

```bash
git checkout master

git pull origin master
```

- Switch back to working branch

```bash
git checkout <new_feature_branch_name>
```

- Rebase with master and resolve conflict if any

```bash
git rebase master
```

- Push changes to new branch on remote

```bash
git push origin <new_feature_branch_name>
```

