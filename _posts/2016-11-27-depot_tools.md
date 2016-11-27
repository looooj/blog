---
layout: post
title: how to config depot_tools user proxy
category: depot_tools
tags: [depot_tools]
---

g.bat

    set HTTP_PROXY=http://proxy_host:port
    set HTTPS_PROXY=http://proxy_host:port
    set PATH=x:\your_path\depot_tools;%PATH%
    gclient


add .\depot_tools\.gitconfig

    [http]
	proxy = http://proxy_host:port
    [https]
	proxy = http://proxy_host:port

    
