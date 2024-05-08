---
title: Openp2p-Launcher-MC帮助文档
date: 2024-04-15 21:55:41
tags:
- 教程
- 工具
---
## 详细
* [![github](https://img.shields.io/badge/Github-Openp2p%20Launcher-Green?logo=github)](https://github.com/Guailoudou/openp2p-launcher/tree/mc) 
* [![issues](https://img.shields.io/badge/Github-issues-Green?logo=github)](https://github.com/Guailoudou/openp2p-launcher/issues) 
* [![在b站关注我](https://img.shields.io/badge/bilibili-%E4%B9%96%E6%BC%8F%E6%96%97-pink?logo=bilibili&logoColor=#00A1D6)](https://space.bilibili.com/496960407)

这是一款p2p的mc联机工具，世界直接出现在局域网，无需输入服务器地址，本程序基于[openp2p](https://github.com/openp2p-cn/openp2p)，本质为自动生成openp2p的配置文件，使用公共账户简化其使用，添加针对mc的功能，本程序开源，使用c++编写

UI版详见[【推荐】UI版-WPF](/2024/04/19/opl_ui/)

直连的连通性依赖于nat类型，具体条件见下面的[nat连通性](#user-content-nat连通性),使用用户**多**的时候不满足条件的也可以连上（中转） 仅直连条件下可以达到**理论最低**延迟

查毒报告(内有行为分析，觉得不安全可以看看，文件已同步至0.5.6.3于2024-2-2上传)：
[微步沙箱 -x64](https://s.threatbook.com/report/file/c1a5f05f2d383506c0dcae99682b01fcca29f9033bdd92ccbb91e4602465b78d)  
[微步沙箱 -x86](https://s.threatbook.com/report/file/493ed1b963b870d953c8818b9a565c5837043b81ead8286922a26f3ecc0c3cca)
* [报毒问题](#报毒问题)
  
使用方法根据提示输入即可，记得要**回车**。遇到问题可进群询问`873968900`（QQ）～ 

**转发给别人软件请不要连bin文件夹一起转发**
**转发给别人软件请不要连bin文件夹一起转发**

[视频演示](https://www.bilibili.com/video/BV11P411a7dH/)

## 下载地址
- mc专用版
MD5值可以通过cmd在文件目录运行`certutil -hashfile 文件名 MD5`查看

|下载地址|MD5|
|---|---|
|[【推荐】UI版-WPF](/2024/04/19/opl_ui/)|基于.net4.7.2全新UI操作页面 功能更加丰富，提供预设功能,连接状态更加直观，自动静默更新|
|[Download-0.5.6.3win-x64](https://gld.lanzoul.com/iMhnx1mzgo1a)|e3696937a3d4b1baff8bf8c65cb58dd8|
|[Download-0.5.6.3win-x86](https://gld.lanzoul.com/i78cA1mzgo9i)|171a63253a52d0a953c25a4f0e60716e|
 or
|[releases](https://github.com/Guailoudou/openp2p-launcher/releases)|注意系统位数x64容易报毒，可下x86遇到问题可进群询问`873968900`（QQ）|
|[Download](https://gld.lanzoul.com/itZPD14z08qf)|nat测试工具|
|[Download签名文件](https://gld.lanzoul.com/iQiQ81mn6k1e)|买不起签名，自己签了一个，这个是安装签名到信任的工具，可以一点程度上降低报毒（效果不明显）|
---
- 其他版本（**玩mc不要下这个，这个版本不推荐使用，如果有其他连接需求可直接使用openp2p**）
  [Download-0.6.2win-x64](https://gld.lanzoul.com/icL0614z09ej)
## 使用方法（0.5）
被连接的输入**0**然后**回车**即可,然后把你的**uuid**和**游戏端口**发给要连接的人

连接的，输入**1或2**（tcp1，udp2，mc，泰拉瑞亚用1，幻兽帕鲁类用2）然后输入**对方uuid**和游戏**对外开放的端口**,连接成功后程序会显示连接成功，直接通过局域网进入即可。

出现`系统无法执行指定的程序`为被杀毒软件拦截，请关闭查毒软件后重启程序，或参考下面为程序目录添加白名单

***连接端口默认为原端口-1，连接ip为 `127.0.0.1`***

使用1或2运行一次之后，会在同目录创建一个以tcp udp uuid和端口命名的快捷方式，可以通过运行快捷方式快速启动，可以通过右键快捷方式->目标，修改尾部端口数字来修改端口号，uuid也可以在这里修改，0.5.6.2开始，最后加个1为udp隧道

**请不要把你的uuid随便发给不认识的人**，可能存在计算机被入侵的可能，不小心泄露uuid了可以通过删除bin文件夹重置uuid

![jyw](https://fastly.jsdelivr.net/gh/Guailoudou/urlimg@main/jyw.png)
![link](https://fastly.jsdelivr.net/gh/Guailoudou/urlimg@main/link.png)

## 常见问题
1. 程序显示`**** offline, it will auto reconnect when peer node online`说明对方程序未启动，请让他输入0启动，如果已经确保启动了请重新启动，或检查uuid是否输入正确。
2. ~~联机mc请使用0.5的版本，**连接成功**后世界会直接出现在局域网，这是mc专用版~~ UI版挺好的。
4. 游戏显示`登入失败，无效的会话`：正版验证问题(房主登录了一般就不会出现)，都使用外置登录或加联机模组关闭验证即可（个人推荐外置登录，还能加载皮肤披风,联机模组在新版本中貌似失效了）
5. 直连可行性受nat类型影响，为p2p连接，无中间服务器，具体见下面表格
6. `系统无法执行指定的程序`被杀毒软件拦截了，见下面[杀毒](#user-content-报毒问题)
6. 程序显示`连接成功`但游戏进来显示`连接超时`：检查端口有没有输入错误，核对端口的准确性
6. 反复异常断开连接：添加服务器ip地址，重启程序，刷新出服务器信息再进入
6. 程序显示`ERROR dial tcp 127.0.0.1:*****: connectex:****** No connection could be made because the targ machine actively refused it.`游戏的对外端口不存在或无法访问，检查对方输的端口或重启mc重新获取端口即可
7. 3大运营商（电信 移动 联通）以外的运营商可以放弃尝试了，其他运营商（广电,长城...）基本都是nat4,流量充足可以考虑用流量,或者靠运气连上
7. 连不上可以尝试参看这个教程进行nat类型优化 [如何提升NAT类型?](https://zhuanlan.zhihu.com/p/338917185)
7. 报错：`ERROR listen error:listen tcp :*****: bind: An attempt was made to access a socket in a way forbidden by its access permissions.`打开`bin`文件夹，打开`config.json` -> 修改`SrcPort`参数为任意其他数字，推荐`25565-25665`之间的，然后直接打开`openp2p.exe`，再通过`127.0.0.1:刚才改后端口` 添加服务器后刷新出服务器信息再进入游戏
7. 更多常见问题等你来[反馈](#user-content-问题反馈)
网上看到的，觉得说得很对~
<img src="https://fastly.jsdelivr.net/gh/Guailoudou/urlimg@main/tw.png" width="100%" alt="说的很对">

## nat连通性
**优化手段**：可以通过在路由器/光猫开启upnp功能，以及设置DMZ主机的方式提高nat环境（光猫需要超级管理员账户密码）
nat类型可在程序刚刚开始运行时看到，为`NATtype`（不太准）
连不上可以尝试参看这个教程进行nat类型优化 [如何提升NAT类型?](https://zhuanlan.zhihu.com/p/338917185)
|nat类型|nat值|
|---|---|
|Full cone NAT（全锥形NAT）|nat1|
|Port Restricted Cone NAT（端口受限锥形NAT）|nat2|
|Restricted Cone NAT（地址受限锥形NAT）|nat3|
|Symetric NAT（对称NAT）|nat4|

|nat值|nat1|nat2|nat3|nat4|
|---|---|---|---|---|
|nat1|✔️|✔️|✔️|✔️|
|nat2|✔️|✔️|✔️|✖️|
|nat3|✔️|✔️|✖️|✖️|
|nat4|✔️|✖️|✖️|✖️|
- ✔️代表可以建立直连，✖️不代表一定连不上，仅连接时间可能较长
## 报毒问题
- 程序安全无毒，程序完全开源，但因为没有软件代码证书，所以非常容易报毒（就输出个hello world放其他人电脑上都报毒）
- 系统自带安全程序报毒：
Windows安全中心->病毒和威胁防护->“病毒和威胁防护”设置->管理设置->排除项->添加或删除排除项->添加排除项->文件夹，然后选择存放程序的上一级文件夹
或安装火绒顶掉，火绒不报毒
- 其他报毒：
我无其他杀毒软件，大体和上面一致，就是把放程序那个文件夹添加到信任或排除，或安装火绒顶掉，火绒不报毒
- 实在不行下x86（32位），这个报毒率低（我也不理解原理，代码一模一样）
## 更新日志
> 之后的写这里，之前的懒得搬过来了
### 2024-1-29 v0.5.6.3
- 修复udp模式下连接成功后无中文提示的bug
### 2024-1-22 v0.5.6.2
- 添加模式2为udp隧道
- 在新生成的快捷方式头部添加隧道类型（tcp/udp）与以前的兼容
- 快捷方式目标最后面添加1为udp隧道
- 支持了单udp连接，连接的快捷方式与以前的兼容（支持upd的游戏啦~）
- 修改了本地端口规则为默认-1
### 2023-11-30 v0.5.6.1
- 修复部分情况下程序中文显示乱码的问题
- 修复0模式下无法正确接收openp2p版本更新的问题
### 2023-11-6 v0.5.6.0
- 去除了模式2，以快捷方式替代
- 现在使用模式1连接后会自动生成一个快捷方式在同目录，快捷方式的路径后部可以直接更改端口，使用快捷方式打开，免输入参数
- 去除了反复的`连接成功`，`连接中`的提示
- 增加了程序图标，版本信息等
### 2023-10-5 v0.5.5.3
- 修复了一个陈年的，几乎没触发过的bug
- 添加了部分可被推送openp2p更新的功能（未完成）
- 学Java去~ 计划之后用Java再写一次，终极目标直接写成mod集成在mc（~画大饼~） 
### 2023-9-5 v0.5.5.2
- 同步了openp2p版本到3.10.9，连接成功率大大提升，升级请删除bin文件夹内的openp2p文件
- 增加了个小提示
### 2023-9-3 v0.5.5
- 今天是我生日嘞，学校网烂github延后上传
- 修改了多线程运行逻辑，现在连接成功之后才会出现在局域网
- 优化了显示是文字，将`sever not online`替换为`连接中...`
### 2023-8-23
- 现在有了支持x86的版本
### 0.5版本功能
- 0.5.3.4同步了openp2p版本到3.10.3(更新版本需要删除以前的bin/openp2p文件)
- 世界直接出现在局域网，无需输入服务器地址
- 支持连接的免登录，房主得登录，可使用[外置登录](https://littleskin.cn)
- 操作简单
## 问题反馈
- 遇到问题可入群反馈`873968900`
- 也可以在这里提出你的建议
[![issues](https://img.shields.io/badge/Github-issues-Green?logo=github)](https://github.com/Guailoudou/openp2p-launcher/issues)


## 其他
- littleskin皮肤站
  [![pcl2](https://img.shields.io/badge/link-littleskin-Green?logo=minetest)](https://littleskin.cn)
- pcl2下载地址
 [![pcl2](https://img.shields.io/badge/link-PCL2-Green?logo=windows)](https://afdian.net/p/0164034c016c11ebafcb52540025c377)
- HMCL下载地址
 [![HMCL](https://img.shields.io/badge/link-HMCL-Green?logo=windows)](https://hmcl.huangyuhui.net/download/)
- BakaXL下载地址
 [![BakaXL](https://img.shields.io/badge/link-BakaXL-Green?logo=windows)](https://www.bakaxl.com/)

## 爱门！！
~~发病ing~~

> 某一日，祂从天坠落&#9834;
  人们抬头仰望，于是看见了星空&#9834;
  星月送来神的女儿，她愿成为人的伴侣&#9834;
  长风化作她的轺车，四海落成她的园圃&#9834;鸟雀衔来善的种子，百花编织爱的颂歌&#9834;
  她便是这样降生于世，行于大地，与人类一同长大，与世界一起发芽&#9834;
  而今，终焉之时将至&#9834;
  而今，归去之时已至&#9834;
  就此告别吧，美丽的世界&#9834;
  此后，将有群星闪耀，因为我如今来过&#9834;
  此后，将有百花绽放，因为我从未离去&#9834;
  请将我的箭、我的花、与我的爱，织成新生的种子，带向那枯萎的大地&#9834;
  然后，便让它开出永恒而无瑕的…人性之华吧&#9834;
  我名为爱莉希雅&#9834;
  最初的律者，人之律者&#9834;
  ![爱莉希雅](https://fastly.jsdelivr.net/gh/Guailoudou/urlimg@main/bh3ali.png)
---
![hli](https://api.xingzhige.com/API/yshl/)
©2023 guailoudou