---
layout: post
title: cmake mingw curl
category: cmake
tags: [cmake]
---


compile curl with cmake mingw error


     list_spaces_append_once(CMAKE_C_STANDARD_LIBRARIES wsock32.lib ws2_32.lib)  # bufferoverflowu.lib

change to 

     if(MINGW)
     list_spaces_append_once(CMAKE_C_STANDARD_LIBRARIES)  # bufferoverflowu.lib
     else()
     list_spaces_append_once(CMAKE_C_STANDARD_LIBRARIES wsock32.lib ws2_32.lib)  # bufferoverflowu.lib
     endif()




