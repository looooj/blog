---
layout: post
title: compile openssl bcb6
---
openssl 版本是0.9.8zb
1) 修改 sys/timeb.h,在ftime定义下面添加下面2行

    #define _timeb timeb
    #define _ftime ftime

2）安装perl之后，在openssl目录下执行

    ms\bcb4.bat
    make -f bcb.mak

3) bcb.mak 

    修改INSTALLTOP=x:\opensslb
    修改*.[ch]  -> *.*
-
4) make install


LFLAGS=-ap -Tpe -x -Gn -w-dup
