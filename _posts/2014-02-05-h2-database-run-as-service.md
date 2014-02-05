---
layout: default
title: h2 database run as service
---
#{{ page.title }}
1) 下载 procrun

    参见<http://commons.apache.org/proper/commons-daemon/procrun.html>

2) 安装 inst.bat
    
    set H2_BASE_DIR=d:\db
    set H2_JAR=D:\java\h2\bin\h2-1.3.170.jar
    set H2_LOG=D:\java\h2\logs

    prunsrv   //IS//h2db --LogPath "%H2_LOG%"  --StartClass org.h2.tools.Server --StopClass org.h2.tools.Server  --StartMode java --Classpath %H2_JAR%  --JvmOptions -Dh2.baseDir=%H2_BASE_DIR% --StartParams "-tcp";"-tcpPort";"1078";"-tcpAllowOthers";"-tcpPassword";"1234" --StopParams "-tcpShutdown";"tcp://localhost:1078";"-tcpPassword";"1234"



*JAVA_HOME环境变量 必须已经设置*

3）启动 

    net start h2db

4）停止

    net stop h2db
  

