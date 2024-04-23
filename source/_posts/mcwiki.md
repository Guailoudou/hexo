---
title: mcwiki从fandom自动跳转到新wiki的Header Editor规则
date: 2024-02-28 19:53:33
tags: 教程
---
mcwiki进行了迁移，但是部分搜索引擎搜索出来依然是fandom的地址，使用如下规则可以访问fandom的地址后自动跳转到行站的地址

- 下载Header Editor扩展之后新建规则，安装如下填写
![img](e584cbe3b84c2c5613e45a3f049b887f496960407.png)
```
^http(s?)://(?:minecraft\.|)fandom\.com(.*)/wiki/(.*)
```
```
https://zh.minecraft.wiki/w/$3
```

- 效果演示：
![gif](24da33d6b7033c8fd97619ebd0047548496960407.gif)

