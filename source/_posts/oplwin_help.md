---
title: 联机工具常见问题
date: 2024-07-12 17:06:46
tags: 
- 教程
- 联机
- 文档
---
本文档为[联机工具](https://blog.gldhn.top/2024/04/19/opl_ui/)常见问题自查文档

### MC登入失败，无效的会话

原因：正版验证导致的

解决方法：都使用外置登录或加联机模组关闭验证（使用外置登录可不关闭正版验证）

ps：个人推荐外置登录，还能加载皮肤披风，以下为设置外置登录的方法

- pcl ：版本设置->设置->服务器->登录方式->第三方登录：AuthlibInjector或LittleSkin->设置为littleskin->返回主页注册或登录
- hmcl ：账户 -> 选择littleskin(没有点下面添加认证服务器，填入https://littleskin.cn/api/yggdrasil) -> 注册或登录

### MC 未知主机

原因：ip格式错误

解决方法：注意IP中间的`:`需要使用英文键盘，不是`：` 

如：应该是`127.0.0.1:25565` 而不是 `127.0.0.1：25565`

ps：为什么不直接复制呢

### Invalid characters in username

进入报错 `Internal Exception:javalang.IllegalStateException:Invalid characters in username`

原因：用户名不合规

解决方法：更改用户名，要求仅可出现英文大小写，数字，英文下划线，3-16位，**不可使用中文用户名**

### MC联机皮肤不显示

原因：关闭正版验证之后不连接验证服务器了，皮肤的验证服务器传递的

解决方案：开启正版验证或加万用皮肤补丁mod 

ps：推荐直接外置登录，在皮肤站设置皮肤就行了

### 添加白名单/报毒/无法启动
原因：内网穿透类软件常被黑客用于攻击企业内网，因此常常被报毒

Windows安全中心->病毒和威胁防护->“病毒和威胁防护”设置->管理设置->排除项->添加或删除排除项->添加排除项->文件夹 选择安装目录中的bin文件夹

默认安装目录：`C:\Program Files(x86)\Guailoudou\OPL\ `

### 软件连接成功但进不去游戏

确保输入ip正确，特别是其中的`:`不是`：` 

添加服务器，刷新出现服务器信息再进，进不去请自行翻译报错，翻译报错可解决50%问题。

翻译后无法解决请尝试多次进入，查看报错是否相同，相同请检查mod兼容性问题，网查报错原因

### 提示对方不在线

确保房主软件右上角版本号旁边的状态灯为绿色，同时检查uid是否正确.

最好等房主版本号后状态灯变绿后其他用户再启动.

### 提示本地端口被占用

点击编辑，更换对应本地端口（比如+1 或 -1）

### 提示网络请求失败

尝试下载自动设置hosts包并执行，如果还是这样，请检查是否被杀毒软件拦截网络请求

### 什么是共享带宽

共享带宽是共享给别人的，当其他用户p2p连不上，而他们都可以与你进行p2p连接时，他们将通过你中转数据，而这中转的数据带宽上限就是你设置的共享带宽，建议保持默认值即可，一般来说只有nat1是有效共享

### Windows无法访问指定设备、路径或文件。你可能没有适当的权限访问该项目。

原因：系统权限不足

解决方法：法1-移动到D盘或其他非C盘打开    法2-参考 [链接](https://blog.csdn.net/datarecover/article/details/128947235) 提权