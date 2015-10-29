---
layout: post
title: compile chromium win7
category: chromium 
tags: [chromium]
---



vs2031 and  windows sdk 10

1) 如果下载svn_bin.zip 和 git-1.9.5.chromium.6_bin.zip失败可以手动下载.把下载命令替换为copy

2) 设置代理如果需要
       
    set HTTP_PROXY=http://proxy:port
    set HTTPS_PROXY=http://proxy:port

3) warn 4819 的问题

      warning C4819: The file contains a character that cannot be represented in the current code page (936). Save the file in Unicode format to prevent data loss
大部分文件都是注释中包含了特殊字符，可以忽略的
在执行python build\gyp_chromium之前,  替换*.gypi   'WarnAsError': 'true' -> 'WarnAsError': 'false'

 src\components\autofill\core\browser\autofill_regex_constants.cc 需要处理，手动另存为utf-8 bom 格式



    set GYP_MSVS_VERSION=2013
    set GYP_GENERATORS=msvs-ninja,ninja
    set PATH=C:\projects\cefsrc\depot_tools;%PATH%
    set DEPOT_TOOLS_WIN_TOOLCHAIN=0
    set GYP_DEFINES=windows_sdk_path="C:\Program Files (x86)\Windows Kits\10"    
    cd c:\projects\cefsrc

    python build\gyp_chromium

    ninja -C out/Debug chrome    




