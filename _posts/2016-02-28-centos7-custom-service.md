---
layout: post
title: centos 7 custom start shutdown service
category: centos7
tags: [centos7]
---

touch /lib/systemd/system/my-custom.service

vim /lib/systemd/system/my-custom.service

    [Unit]
    Description=Custom Start and Shutdown
    After=syslog.target
    After=network.target


    [Service]

    Type=oneshot
    ExecStart=/opt/app/scripts/sys-start.sh
    ExecStop=/opt/app/scripts/sys-shutdown.sh
    RemainAfterExit=yes

    [Install]
    WantedBy=multi-user.target


sys-start.sh

    #!/bin/sh
    #...
    date>/opt/app/scripts/sys-start.txt

sys-shutdown.sh

    #!/bin/sh
    #...
    date>/opt/app/scripts/sys-shutdown.txt



systemctl enable my-custom.service




from [https://ubuntu.flowconsult.at/linux/ubuntu-15-04-startup-shutdown-script-systemd/]
