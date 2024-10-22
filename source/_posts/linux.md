---
title: linux指令
date: 2024-03-27 18:10:13
tags:
---
这里是部分常用的linux指令，仅个人记录备份使用，仅供参考

防火墙：`firewall-cmd --zone=public --add-port=80/tcp --permanent `

重启防火墙：`firewall-cmd --reload`

查看端口：`netstat -antp | grep 80`

删除文件 `rm ./123`

删除文件夹 `rm -rf html` （-r递归删除，删所有子目录，-f强制删除，无提示）

打开路径`cd html`

查看目录 `ls`

创建文件夹 `mkdir html`

创建文件 `touch index.html`

写入内容 `echo "hello world" > index.html`

下载文件 `wget https://www.baidu.com` 

移动/(重命名)文件 `mv index.html index.html`

复制文件 `cp in.c inn.c`

软连接 `ln -s in.s inn.s`


