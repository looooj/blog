---
layout: post
title: cmake libssh2
category: cmake 
tags: [cmake,libssh2]
---

\libssh2-master\src\libssh2_config_cmake.h.in

insert after #include <stdarg.h>
    
    #if _MSC_VER < 1500
    #define vsnprintf _vsnprintf
    #endif





