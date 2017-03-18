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
