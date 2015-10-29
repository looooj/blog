---
layout: post
title: oracle sql page
category: oracle 
tags: [oracle]
---



    select *
      from (select *
          from (select t.*, row_number() OVER(ORDER BY null) AS "row_number"
                  from tb_task t) p
         where p."row_number" > 5000) q
      where rownum <= 300



来源 http://www.cnblogs.com/xiaopang2010/archive/2012/07/23/2604880.html




