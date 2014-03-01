---
layout: post
title: cygwin install gitolite
tags: [cygwin,gitolite] 
----


linux下安装不同之处

##sshd安装

需要安装 openssh git cygwin package
cygwin环境下执行

    ssh-host-config -y


##git用户的创建

windows用户管理创建用户git

cygwin环境下执行

    mkpasswd -l -u git >>/etc/passwd


其他的步骤和标准流程都一样


打开 msysgit bash

生成 key

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

退出host，配置 ~/.ssh/config ( c:\users\username\.ssh )

    host local-git-admin
        hostname localhost-ip
        user admin
        IdentityFile /path-to/admin


clone

    git clone git@local-git-admin:gitolite-admin

     
 