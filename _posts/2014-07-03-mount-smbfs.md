---
layout: post
title: mount smbfs with read/write permissions for a non-root user
tags: [mount] 
---

mount smbfs 默认是root,加上uid和gid参数
    
    
     
    mount -t smbfs //host/share /home/user/share -o uid=501,gid=501,rw,username=user,password=password



