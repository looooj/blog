---
layout: post
title: oracle kill dbms job
category: oracle 
tags: [oracle]
---

1) find sid and serial#

     
    Select a.*, b.serial#  From Dba_Jobs_Running a,  v$session b
    Where a.sid = b.sid
    



2) ALTER SYSTEM KILL Session 'sid,serial#'

     
    ALTER SYSTEM KILL Session '1014,54404';








