---
layout: post
title: eclipse git gitolite tips
tags: [eclipse,git,gitolite]
---

##eclipse git push

eclipse 的新建项目egit不能push, 只要通过其他工具push一次就可以了, project/.git/config文件会增加以下内容

    [remote "origin"]
    url = ssh://git@host/project
    fetch = +refs/heads/*:refs/remotes/origin/*


##.ssh/config ##

    host xxx
        hostname xxx.net
        user alice
        IdentityFile c:/Users/user/.ssh/git/dev1



##gitolite conf

    repo projectname 
       RW+         = @develop
       RW          = alice
       R           = @all 
       RW+ develop = bob

    repo project_name
      权限 [分支名称] = 分组 用户

基本授权配置
   
     repo parent_dir/[a-zA-Z0-9].*
       C = @develop

配置@develop组创建repo


    @develop = alice @admin

分组可以嵌套, repo 也可以使用分组表示

@all 所有用户


RW+ push any
RW 
  
##git config

    [user]
     name=
     email=

~/.gitconfig 用户配置文件位置

.git/config 当前项目配置 


##new repo

    git init

    git remote add origin git@host:project_path

    git push origin master
