---
layout: post
title: compile curl bcb6
---


    cd curl-7.37.1
    md bcb
    cd bcb
    cmake -G "Borland Makefiles"  ..\  
    make -f Makefile

会报告编译错误

修改curl_config.h,追加以下
    
    #define ssize_t  int
    #define SIZEOF_SIZE_T 4
    #define HAVE_UTIME_H 1


