---
layout: post
title: local ssh remote server
tags: [ssh,socat]
---

local http server 在内网

remote server 在外网

需要在remote server 访问 local server http 服务


    ssh -R 7001:localhost:80 -i your_id user@remote


在remote server
  
    curl http://localhost:7001
      <!DOCTYPE html>
      ...



    socat tcp:localhost:7001 tcp-listen:7002,reuseaddr,fork

    curl http://remote:7002

