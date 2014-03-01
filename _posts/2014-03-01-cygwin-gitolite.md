---
layout: post
title: Cygwin install gitolite
tags: [cygwin,gitolite] 
----


和linux不同之处是

##ssh安装

cygwin环境下执行

    ssh-host-config -y


##git用户的创建

windows用户管理创建用户git

cygwin环境下执行

    mkpasswd -l -u git >>/etc/passwd


其他的步骤和标准流程都一样

     
 