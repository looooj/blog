---
layout: post
title: window event message
category: mc
tags: [mc]
---

1)
g.mc

    MessageIdTypedef=WORD

    LanguageNames=(
        English=0x409:MSG00409
    )

    MessageId=1
    SymbolicName=GENERAL_MSG
    Language=English
    %1
    .

2) mkmc.bat

    mc.exe %1.mc
    rc.exe /r  %1.rc
    link.exe -dll -noentry %1.res

3) sdk 或 vc 加入路径 执行 mkmc g, 生成g.dll


4) 注册 g.dll

     create key  
     SYSTEM\\CurrentControlSet\\Services\\EventLog\\Application\\AppName

     value REG_EXPAND_SZ EventMessageFile  /pathto/g.dll
     value REG_DWORD  TypesSupported  7

5) report event message

     mHandle = ::RegisterEventSource(NULL, appName);    
     ::ReportEvent(mHandle, // event log handle
                    error_type, // event type
                    0, // category zero
                    1, //  MessageId=1
                    NULL, // no user security identifier
                    1, // one substitution string
                    0, // no data
                    (const char**)msg, // pointer to string array
                    NULL);
    DeregisterEventSource(mHandle);
