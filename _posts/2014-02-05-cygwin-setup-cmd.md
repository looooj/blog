---
layout: markdown
title: Cygwin 命令行自动安装说明
---
#{{ page.title }}



创建下载目录 d:\prog\cy (个人习惯的cy下载目录)

***pkg.bat***

    set CYGWIN_ROOT_DIR=d:\prog\cygwin
    set CYGWIN_LOCAL_DIR=d:\prog\cy\dl
    set CYGWIN_SITE_URL=http://mirrors.163.com/cygwin
    :check_params
    if "%~1" == "" goto end
    setup-x86.exe -D -q -a x86 -O -d -l %CYGWIN_LOCAL_DIR% --root %CYGWIN_ROOT_DIR% -s %CYGWIN_SITE_URL% -P %1
    setup-x86.exe -L -a x86 -q -d -l %CYGWIN_LOCAL_DIR% --root %CYGWIN_ROOT_DIR% -s %CYGWIN_SITE_URL% -P %1
    shift
    :goto check_params

    :end
    



call pkg.bat openssh 

常用的安装包名称
    bash gcc gcc-g++ openssh expect python git curl vim cygrunsrv

更多安装包名称在<http://cygwin.com/packages/>

查找app在哪个package

    cygcheck -p app