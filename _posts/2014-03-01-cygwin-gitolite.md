---
layout: post
title: Cygwin install gitolite
tags: [cygwin,gitolite] 
----


linux下安装不同之处

##ssh安装

cygwin环境下执行

    ssh-host-config -y


##git用户的创建

windows用户管理创建用户git

cygwin环境下执行

    mkpasswd -l -u git >>/etc/passwd


其他的步骤和标准流程都一样




打开msysgit bash

生成key

    ssh-keygen -N '' -f admin
    
上传到host

    scp admin.pub git@host:~/
    
登录host

    ssh git@host
    
安装

    git clone git://github.com/sitaramc/gitolite
    mkdir -p ~/bin
    gitolite/install -to ~/bin
    gitolite setup -pk admin.pub
    exit

退出host，配置 ~/ssh/config

    host local-git-admin
        hostname 192.168.0.20
        user admin
        IdentityFile /path-to/admin


clone

    git clone git@local-git-admin:gitolite-admin

     
 