---
title: git版本回退
date: 2017-09-12 15:56:26
tags: git
categories: 开发工具
---

# reset

回退git的版本提交的commit

参数:

—soft: 只改变本地仓库的提交点，而暂存区和工作区都不改变

—mixed: 改变本地仓库和暂存区，工作区不变

—hard: 本地仓库、暂存区、工作区全部改变

```shell
#回退最新的修改
git reset --hard HEAD^
git reset --hard HEAD~3
#回退哈希值为3628164...的修改，注意3628164...之后的也被改变
git reset --hard 3628164
```

# revert

回退git的版本，并把这次的回退作为一次修改提交。

用法同reset

# 远程仓库回退

1. 在本地用resert，然后提交到远程仓库。（推荐）
2. 在本地用reset，然后用`git push --force`。
3. 在本地用reset，然后用删除远程的master分支`git push origin :master`，重建master分支`git push origin master`。

# 问题

1. 如果回退之后，又觉得以前写的是正确的，这次的回退是误操作，那怎么办呢?

```shell
#查看自己的电脑上的操作哈希值
$ git reflog
#再重新调整git的HEAD
$ git reset --hard a123456
```

