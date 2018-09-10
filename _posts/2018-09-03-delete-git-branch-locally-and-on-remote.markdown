---
title: Delete git branch locally and on remote
layout: post
date: '2018-09-03 20:27:00 +0530'
categories: version-control git
---

This is my method to remove a branch permanently.

First delete the branch from github server.
Then in local run the following command

```
git branch -d branch_name
git branch -D branch_name
```

The -d option stands for --delete, which would delete the local branch, only if you have already pushed and merged it with your remote branches.

The -D option stands for --delete --force, which deletes the branch regardless of its push and merge status, so be careful using this one.

After choosing between one of the above commands ... You need to pull changes from server and then run this command to remove all the branches that has been deleted from the server.

```
git fetch --all --prune
```