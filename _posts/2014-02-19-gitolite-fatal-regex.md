---
layout: post
title: gitolite FATAL: Nested quantifiers in regex
tags: [gitolite FATAL]
---

由于正则表达式书写错误gitolite-admin/conf/gitolite.conf ，gitolite提示错误

    FATAL: Nested quantifiers in regex; marked by <-- HERE in ... <-
 .$/ at /home/git/bin/lib/Gitolite/Conf/Load.pm line 348, <DATA> line 1.

不能push

查看gitolite服务端发现gitolite.conf实际转换成 gitolite.conf-compiled.pm（/home/git/.gitolite/conf目录),手工编辑gitolite.conf-compiled.pm去掉出错的repo定义，然后就可以提交了







