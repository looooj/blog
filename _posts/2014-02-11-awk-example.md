---
title: awk 使用
layout: post
tags: [awk]
---

awk /模式，命令/ 文件

例1 提取包含ABCD开头的7个字符


    2014/02/07  08:26    <DIR>          XXXABCD-123XXXX
    
    awk '/ABCD|abcd/ {print substr( $4, index(toupper($4),"ABCD"),7 ) }'  /cygdrive/t/t1.txt






