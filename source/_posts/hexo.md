---
title: hexo使用指令记录
date: 2022-02-30 17:13:27
tags: 日志
comments: false
---
这是本人使用日志，仅供本人参考使用 日期的假的

使用cmd在根目录运行：`D:\web\pages`

- 构建网页 构建到`public`
```
hexo g 
```

- 新建md 到`source`
```
hexo new -p <文件名> "<标题>"
```

- 本地服务端映射 `7000`端口
```
hexo s
```

- 清理数据（使用后需要重新构建，需要提前备份git数据）
```
hexo clean
```