---
layout: post
title: git submodule
category: git
tags: [git]
---

1) git submodule add git@local-git:commons/c-utils src/utils
- git submodule 要求top-level目录下操作

2) git submodule init
- 第一次
- 要求top-level目录下操作

3) git submodule update --recursive --remote

4) git status 检查 submodule 的分支

5) “submodule 项目和它的父项目本质上是 2 个独立的 git 仓库”,
来自http://blog.devtang.com/2013/05/08/git-submodule-issues/
