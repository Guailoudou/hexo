---
title: OPL_WPF帮助文档
date: 2024-04-19 20:17:33
tags:
- 教程
- 工具
---
# 下载

免安装版如果要换安装版，把原来地址的bin/config文件移动到安装目录的系统地方就可以继续用之前的uid和隧道

支持 win10-win11，win10以下版本需要另外安装[.NET Framework 4.7.2](https://dotnet.microsoft.com/zh-cn/download/dotnet-framework/net472)

自动静默更新，后续无需手动更新

### 下载源1（推荐）：

- [夸克](https://pan.quark.cn/s/8537690fd74b) 
  
夸克每转存一次，我可以获得0.2软妹币，所以推荐使用这个

下面的下载方式都可以直接免登录直接下载，其中蓝奏云下载较快

### 下载源2（可能较慢）：

- 安装包（小白下这个）：[OPL_Setup.msi](https://file.gldhn.top/file/OPL_Setup.msi)   
- 免安装版：[OPL联机工具UI.zip](https://file.gldhn.top/file/OPL联机工具UI.zip)

### 下载源3（仅msi安装包）：

- [蓝奏云](https://gld.lanzoul.com/i30R7228ts5a)  

# 使用方法

1. 下载后安装或解压，双击 OPL_WpfApp.exe 或 点击桌面快捷方式启动
2. 被连接的仅需要在无隧道启用情况下直接启动即可（虽然启用也行，但不建议），然后向需要连接你的人提供你的UID和端口号即可
3. 连接的需要新建隧道，新建隧道时需要输入被连接者的UUID和端口号（远程端口）本地端口可根据情况随意（默认相同），协议根据情况选择（MC为TCP），然后点击新建
4. 根据情况启用隧道，运行过程中会锁定软件，无法操作，连接成功的隧道状态灯会变绿
5. 预设功能为一些固定端口的程序，如果你还知道其他固定端口的，可以提交给作者添加（该列表为联网更新）

MC-<a href="https://minecraft.net"><img src="https://www.minecraft.net/content/dam/minecraftnet/games/minecraft/logos/Global-Header_MCCB-Logo_300x51.svg" title="MC" style="width: 100px;"></a>使用看[这里](/2024/04/22/opl_mc/)，其他的也可以参考

**注意，是连接的添加隧道，不是被连接的！！**

# 常见问题

### 点击启动后程序闪退/显示报毒：

Windows安全中心->病毒和威胁防护->“病毒和威胁防护”设置->管理设置->排除项->添加或删除排除项->添加排除项->文件夹 选择安装目录中的`bin`文件夹
默认安装目录：`C:\Program Files(x86)\Guailoudou\OPL\`

### 无法获取预设/更新/下载慢：

下载此文件，解压后运行（自动检索最佳cdn的ip并自动设置hosts）：

- [夸克网盘](https://pan.quark.cn/s/2c923c5f82d5)
- [Sethosts.zip](Sethosts.zip) -本站下载

# 预设功能(自动同步软件中的列表)

<iframe src="https://file.gldhn.top/web/preset/?type=preset" width="100%" height="225px" frameborder="0" scrolling="yes"></iframe>

如果你知道更多固定端口的游戏，请提交给我，谢谢，理论能用frp（樱花frp那种）连的游戏都可以用

# 日志（自动同步软件中关于内日志）

<iframe src="https://file.gldhn.top/web/preset/?type=uplog" width="100%" height="235px" frameborder="0" scrolling="yes"></iframe>

### 充电/发电鸣谢

<iframe src="https://file.gldhn.top/web/thank/" width="100%" height="225px" frameborder="0" scrolling="yes"></iframe>

<a href="https://afdian.net/a/guailoudou"><img src="https://pic1.afdiancdn.com/static/img/welcome/button-sponsorme.png" alt=""  style="width: 150px;"></a>


# 开源

- [![Github](https://img.shields.io/badge/Github-OPL_WpfApp-Green?logo=github)](https://github.com/Guailoudou/OPL-WpfApp)
- [![Github](https://img.shields.io/badge/Github-openp2p-Green?logo=github)](https://github.com/openp2p-cn/openp2p)

