---
title: linux指令
date: 2024-03-27 18:10:13
tags:
---
防火墙：`firewall-cmd --zone=public --add-port=80/tcp --permanent `

重启防火墙：`firewall-cmd --reload`

查看端口：`netstat -antp | grep 80`

删除文件 `rm ./123`

删除文件夹 `rm -rf html`

打开路径`cd html`

查看目录 `ls`

创建文件夹 `mkdir html`

创建文件 `touch index.html`

写入内容 `echo "hello world" > index.html`

下载文件 `wget https://www.baidu.com`

移动/(重命名)文件 `mv index.html index.html`


