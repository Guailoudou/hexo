---
title: OPL_WPF帮助文档
date: 2024-04-19 20:17:33
tags:
- 教程
- 工具
---
## 下载

免安装版如果要换安装版，把原来地址的bin/config文件移动到安装目录的系统地方就可以继续用之前的uid和隧道

支持 win10-win11，win10以下版本需要另外安装[.NET Framework 4.7.2](https://dotnet.microsoft.com/zh-cn/download/dotnet-framework/net472)

遇到问题请先查看常见问题中是否有相关问题：[常见问题](/2024/07/12/oplwin_help/)

遇到问题请先查看常见问题中是否有相关问题：[常见问题](/2024/07/12/oplwin_help/)

遇到问题请先查看常见问题中是否有相关问题：[常见问题](/2024/07/12/oplwin_help/)

自动静默更新，后续无需手动更新

安装包会直接安装到固定路径，创建快捷方式 (安装包存在更新异常问题，暂时不再提供)

免安装版解压就行

单文件版会在打开后自动下载需要的文件
- [![Github](https://img.shields.io/badge/Github-OPL_WpfApp-Green?logo=github)](https://github.com/Guailoudou/OPL-WpfApp)

### 下载源1（推荐）win：

- [夸克](https://pan.quark.cn/s/8537690fd74b) 
  
夸克每转存一次，我可以获得0.2软妹币，所以推荐使用这个

### 下载源2(Gitee) win：
需要登录gitee 
- 免安装版：[OPL联机工具UI.zip](https://gitee.com/guailoudou/urlfile/raw/main/file/OPL联机工具UI.zip)
- 单文件版：[OPL_WpfApp.exe](https://gitee.com/guailoudou/urlfile/raw/main/file/OPL_WpfApp.exe)

### linux系统
运行
```
sudo curl -k -o opl_linux.sh "https://gitee.com/guailoudou/urlfile/raw/main/file/opl_linux.sh" && sudo bash ./opl_linux.sh
```
关闭
```
sudo killall -9 openp2p
```
**注意linux系统暂只支持被连接，且可能存在各种各样的问题，目前仅仅只是能用**
## 使用方法

1. 下载后安装或解压，双击 OPL_WpfApp.exe 或 点击桌面快捷方式启动
2. 被连接的仅需要在无隧道启用情况下直接启动即可（虽然启用也行，但不建议），然后向需要连接你的人提供你的UID和端口号即可
3. 连接的需要新建隧道，新建隧道时需要输入被连接者的UID和端口号（远程端口）本地端口可根据情况随意（默认相同），协议根据情况选择（MC为TCP），然后点击新建
4. 根据情况启用隧道，运行过程中会锁定软件，无法操作，连接成功的隧道状态灯会变绿
5. 预设功能为一些固定端口的程序，如果你还知道其他固定端口的，可以提交给作者添加（该列表为联网更新）

MC-<a href="https://minecraft.net"><img src="https://www.minecraft.net/content/dam/minecraftnet/games/minecraft/logos/Global-Header_MCCB-Logo_300x51.svg" title="MC" style="width: 100px;"></a>使用看[这里](/2024/04/22/opl_mc/)，其他的也可以参考

**注意，是连接的添加隧道，不是被连接的！！**

# 常见问题

### 点击启动后程序闪退/显示报毒：
原因：内网穿透类软件常被黑客用于攻击企业内网，因此常常被报毒

Windows安全中心->病毒和威胁防护->“病毒和威胁防护”设置->管理设置->排除项->添加或删除排除项->添加排除项->文件夹 选择安装目录中的`bin`文件夹
默认安装目录：`C:\Program Files(x86)\Guailoudou\OPL\`

### 更多问题

请移步这里查看：[常见问题](/2024/07/12/oplwin_help/)

# 预设功能(自动同步软件中的列表)

<iframe src="https://file.gldhn.top/web/preset/?type=preset" width="100%" height="225px" frameborder="0" scrolling="yes"></iframe>

如果你知道更多固定端口的游戏，请提交给我，谢谢，理论能用frp（樱花frp那种）连的游戏都可以用

# 日志（自动同步软件中关于内日志）

<iframe src="https://file.gldhn.top/web/preset/?type=uplog" width="100%" height="235px" frameborder="0" scrolling="yes"></iframe>

### 充电/发电鸣谢

<iframe src="https://file.gldhn.top/web/thank/" width="100%" height="225px" frameborder="0" scrolling="yes"></iframe>

<a href="https://afdian.com/a/guailoudou"><img src="https://pic1.afdiancdn.com/static/img/welcome/button-sponsorme.png" alt=""  style="width: 150px;"></a>


# 开源

- [![Github](https://img.shields.io/badge/Github-OPL_WpfApp-Green?logo=github)](https://github.com/Guailoudou/OPL-WpfApp)
- [![Github](https://img.shields.io/badge/Github-openp2p-Green?logo=github)](https://github.com/openp2p-cn/openp2p)

