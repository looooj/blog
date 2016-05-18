---
layout: post
title: how to shred a folder
category: linux
tags: [linux]
---

cd  to your directory then

    find -iname "*" -type f | xargs shred -fuzv


from [http://askubuntu.com/questions/122549/how-to-shred-a-folder]
