---
title: hhvm
date: 2017-05-17 09:57:14
tags:
    -D05
    -Ubuntu
    -CentOS
categories:
    -Estuary
    -Document
---
**Setup:**
    ```bash
    scp xxx@192.168.1.107:~/hhvm.tar .
    tar xf hhvm.tar
    apt-get install nginx -y
    ./start.sh
    ```
**Test:**
    ```bash
    curl ip/echo_test.php
    ```

