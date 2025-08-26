---
title: Minecraft 服务器 JSON-RPC API 文档
date: 2025-08-27 02:59:34
tags: 文档
---
# Minecraft 服务器 JSON-RPC API 文档

**版本：** 1.0.0  
**OpenRPC 版本：** 1.3.2  

该文档内容由AI根据发送`{"id":1,"method":"rpc.discover"}`返回的内容生成。

---

## 概述

本 API 提供了对 Minecraft 服务器的远程管理和监控功能。它遵循 JSON-RPC 2.0 规范，允许客户端通过 RPC 调用查询服务器状态、管理玩家（允许列表、封禁、踢出、操作员）、修改服务器设置和游戏规则等。

---

## 方法 (Methods)

### 服务器管理

#### `minecraft:server/status`

获取服务器当前状态。

- **参数:** 无
- **返回值:**
  - `status` (object): 服务器状态对象
    - `started` (boolean): 服务器是否正在运行
    - `players` (array[Player]): 当前在线玩家列表
    - `version` (object):
      - `name` (string): 服务器版本名称
      - `protocol` (integer): 协议版本号

#### `minecraft:server/save`

保存服务器状态（世界数据）。

- **参数:**
  - `flush` (boolean, required): 是否立即强制写入磁盘
- **返回值:**
  - `saving` (boolean): 保存操作是否已启动

#### `minecraft:server/stop`

停止服务器。

- **参数:** 无
- **返回值:**
  - `stopping` (boolean): 停止操作是否已启动

#### `minecraft:server/system_message`

向服务器或特定玩家发送系统消息。

- **参数:**
  - `message` (SystemMessage, required): 消息对象
    - `message` (Message): 要发送的消息内容
    - `overlay` (boolean): 消息是否显示在屏幕中央（类似标题）
    - `receivingPlayers` (array[Player]): 接收消息的玩家列表。如果为空，则发送给所有玩家。
- **返回值:**
  - `sent` (boolean): 消息是否已成功发送

---

### 玩家管理

#### `minecraft:players`

获取所有当前连接的玩家。

- **参数:** 无
- **返回值:**
  - `players` (array[Player]): 在线玩家列表

#### `minecraft:players/kick`

踢出指定玩家。

- **参数:**
  - `kick` (array[KickPlayer], required): 要踢出的玩家及其原因列表
    - `players` (array[Player]): 被踢玩家
    - `message` (Message): 踢出原因消息
- **返回值:**
  - `kicked` (array[Player]): 成功被踢出的玩家列表

#### `minecraft:allowlist`

获取允许列表。

- **参数:** 无
- **返回值:**
  - `allowlist` (array[Player]): 允许列表中的玩家

#### `minecraft:allowlist/set`

设置整个允许列表（替换现有列表）。

- **参数:**
  - `players` (array[Player], required): 新的允许列表
- **返回值:**
  - `allowlist` (array[Player]): 设置后的新允许列表

#### `minecraft:allowlist/add`

向允许列表添加玩家。

- **参数:**
  - `add` (array[Player], required): 要添加的玩家列表
- **返回值:**
  - `allowlist` (array[Player]): 添加后更新的允许列表

#### `minecraft:allowlist/remove`

从允许列表中移除玩家。

- **参数:**
  - `remove` (array[Player], required): 要移除的玩家列表
- **返回值:**
  - `allowlist` (array[Player]): 移除后更新的允许列表

#### `minecraft:allowlist/clear`

清空允许列表。

- **参数:** 无
- **返回值:**
  - `allowlist` (array[Player]): 清空后的允许列表（应为空数组）

#### `minecraft:bans`

获取用户封禁列表。

- **参数:** 无
- **返回值:**
  - `banlist` (array[UserBan]): 被封禁的用户列表

#### `minecraft:bans/set`

设置整个用户封禁列表（替换现有列表）。

- **参数:**
  - `bans` (array[UserBan], required): 新的封禁列表
- **返回值:**
  - `banlist` (array[UserBan]): 设置后的新封禁列表

#### `minecraft:bans/add`

封禁指定玩家。

- **参数:**
  - `add` (array[UserBan], required): 要封禁的玩家列表
    - `player` (Player): 被封禁的玩家
    - `reason` (string): 封禁原因
    - `expires` (string): 封禁过期时间（ISO 8601 格式，或 "forever"）
    - `source` (string): 执行封禁的来源（如管理员名）
- **返回值:**
  - `banlist` (array[UserBan]): 添加后更新的封禁列表

#### `minecraft:bans/remove`

解除对指定玩家的封禁。

- **参数:**
  - `remove` (array[Player], required): 要解封的玩家列表
- **返回值:**
  - `banlist` (array[UserBan]): 解封后更新的封禁列表

#### `minecraft:bans/clear`

清空用户封禁列表。

- **参数:** 无
- **返回值:**
  - `banlist` (array[UserBan]): 清空后的封禁列表（应为空数组）

#### `minecraft:ip_bans`

获取 IP 封禁列表。

- **参数:** 无
- **返回值:**
  - `banlist` (array[IpBan]): 被封禁的 IP 地址列表

#### `minecraft:ip_bans/set`

设置整个 IP 封禁列表（替换现有列表）。

- **参数:**
  - `banlist` (array[IpBan], required): 新的 IP 封禁列表
- **返回值:**
  - `banlist` (array[IpBan]): 设置后的新 IP 封禁列表

#### `minecraft:ip_bans/add`

封禁指定 IP 地址。

- **参数:**
  - `add` (array[IncomingIpBan], required): 要封禁的 IP 列表
    - `ip` (string): 要封禁的 IP 地址
    - `reason` (string): 封禁原因
    - `expires` (string): 封禁过期时间
    - `source` (string): 执行封禁的来源
    - `player` (Player): 关联的玩家（可选）
- **返回值:**
  - `banlist` (array[IpBan]): 添加后更新的 IP 封禁列表

#### `minecraft:ip_bans/remove`

解除对指定 IP 地址的封禁。

- **参数:**
  - `ip` (array[string], required): 要解封的 IP 地址列表
- **返回值:**
  - `banlist` (array[IpBan]): 解封后更新的 IP 封禁列表

#### `minecraft:ip_bans/clear`

清空 IP 封禁列表。

- **参数:** 无
- **返回值:**
  - `banlist` (array[IpBan]): 清空后的 IP 封禁列表（应为空数组）

#### `minecraft:operators`

获取所有操作员（OP）玩家。

- **参数:** 无
- **返回值:**
  - `operators` (array[Operator]): 操作员列表

#### `minecraft:operators/set`

设置整个操作员列表（替换现有列表）。

- **参数:**
  - `operators` (array[Operator], required): 新的操作员列表
- **返回值:**
  - `operators` (array[Operator]): 设置后的新操作员列表

#### `minecraft:operators/add`

授予玩家操作员权限。

- **参数:**
  - `add` (array[Operator], required): 要授予 OP 权限的玩家列表
    - `player` (Player): 被授予权限的玩家
    - `permissionLevel` (integer): 权限等级 (1-4)
    - `bypassesPlayerLimit` (boolean): 是否绕过玩家数量上限
- **返回值:**
  - `operators` (array[Operator]): 添加后更新的操作员列表

#### `minecraft:operators/remove`

撤销玩家的操作员权限。

- **参数:**
  - `remove` (array[Player], required): 要撤销 OP 权限的玩家列表
- **返回值:**
  - `operators` (array[Operator]): 撤销后更新的操作员列表

#### `minecraft:operators/clear`

撤销所有玩家的操作员权限。

- **参数:** 无
- **返回值:**
  - `operators` (array[Operator]): 清空后的操作员列表（应为空数组）

---

### 服务器设置

#### `minecraft:serversettings/autosave`

获取自动保存是否启用。

- **参数:** 无
- **返回值:**
  - `enabled` (boolean): 自动保存是否启用

#### `minecraft:serversettings/autosave/set`

启用或禁用自动保存。

- **参数:**
  - `enable` (boolean, required): 是否启用自动保存
- **返回值:**
  - `enabled` (boolean): 设置后的新状态

#### `minecraft:serversettings/difficulty`

获取当前游戏难度。

- **参数:** 无
- **返回值:**
  - `difficulty` (string): 难度 ("peaceful", "easy", "normal", "hard")

#### `minecraft:serversettings/difficulty/set`

设置游戏难度。

- **参数:**
  - `difficulty` (string, required): 新的难度级别
- **返回值:**
  - `difficulty` (string): 设置后的新难度

#### `minecraft:serversettings/enforce_allowlist`

获取是否强制执行允许列表（被移除的玩家是否立即被踢出）。

- **参数:** 无
- **返回值:**
  - `enforced` (boolean): 是否强制执行

#### `minecraft:serversettings/enforce_allowlist/set`

启用或禁用允许列表的强制执行。

- **参数:**
  - `enforce` (boolean, required): 是否强制执行
- **返回值:**
  - `enforced` (boolean): 设置后的新状态

#### `minecraft:serversettings/use_allowlist`

获取是否启用了允许列表（仅允许列表中的玩家加入）。

- **参数:** 无
- **返回值:**
  - `used` (boolean): 允许列表是否启用

#### `minecraft:serversettings/use_allowlist/set`

启用或禁用允许列表功能。

- **参数:**
  - `use` (boolean, required): 是否启用允许列表
- **返回值:**
  - `used` (boolean): 设置后的新状态

#### `minecraft:serversettings/max_players`

获取服务器最大玩家数量。

- **参数:** 无
- **返回值:**
  - `max` (integer): 最大玩家数

#### `minecraft:serversettings/max_players/set`

设置服务器最大玩家数量。

- **参数:**
  - `max` (integer, required): 新的最大玩家数
- **返回值:**
  - `max` (integer): 设置后的新最大玩家数

#### `minecraft:serversettings/pause_when_empty_seconds`

获取服务器在无玩家在线时自动暂停前的等待秒数。

- **参数:** 无
- **返回值:**
  - `seconds` (integer): 等待秒数

#### `minecraft:serversettings/pause_when_empty_seconds/set`

设置服务器在无玩家在线时自动暂停前的等待秒数。

- **参数:**
  - `seconds` (integer, required): 新的等待秒数
- **返回值:**
  - `seconds` (integer): 设置后的新等待秒数

#### `minecraft:serversettings/player_idle_timeout`

获取空闲玩家被自动踢出前的秒数。

- **参数:** 无
- **返回值:**
  - `seconds` (integer): 空闲超时秒数

#### `minecraft:serversettings/player_idle_timeout/set`

设置空闲玩家被自动踢出前的秒数。

- **参数:**
  - `seconds` (integer, required): 新的空闲超时秒数
- **返回值:**
  - `seconds` (integer): 设置后的新空闲超时秒数

#### `minecraft:serversettings/allow_flight`

获取是否允许生存模式玩家飞行。

- **参数:** 无
- **返回值:**
  - `allowed` (boolean): 是否允许飞行

#### `minecraft:serversettings/allow_flight/set`

允许或禁止生存模式玩家飞行。

- **参数:**
  - `allow` (boolean, required): 是否允许飞行
- **返回值:**
  - `allowed` (boolean): 设置后的新状态

#### `minecraft:serversettings/motd`

获取服务器的 MOTD（欢迎信息）。

- **参数:** 无
- **返回值:**
  - `message` (string): MOTD 内容

#### `minecraft:serversettings/motd/set`

设置服务器的 MOTD（欢迎信息）。

- **参数:**
  - `message` (string, required): 新的 MOTD 内容
- **返回值:**
  - `message` (string): 设置后的新 MOTD

#### `minecraft:serversettings/spawn_protection_radius`

获取出生点保护半径（以方块为单位）。

- **参数:** 无
- **返回值:**
  - `radius` (integer): 保护半径

#### `minecraft:serversettings/spawn_protection_radius/set`

设置出生点保护半径。

- **参数:**
  - `radius` (integer, required): 新的保护半径
- **返回值:**
  - `radius` (integer): 设置后的新半径

#### `minecraft:serversettings/force_game_mode`

获取是否强制玩家使用服务器默认游戏模式。

- **参数:** 无
- **返回值:**
  - `forced` (boolean): 是否强制

#### `minecraft:serversettings/force_game_mode/set`

启用或禁用强制使用服务器默认游戏模式。

- **参数:**
  - `force` (boolean, required): 是否强制
- **返回值:**
  - `forced` (boolean): 设置后的新状态

#### `minecraft:serversettings/game_mode`

获取服务器默认游戏模式。

- **参数:** 无
- **返回值:**
  - `mode` (string): 游戏模式 ("survival", "creative", "adventure", "spectator")

#### `minecraft:serversettings/game_mode/set`

设置服务器默认游戏模式。

- **参数:**
  - `mode` (string, required): 新的游戏模式
- **返回值:**
  - `mode` (string): 设置后的新游戏模式

#### `minecraft:serversettings/view_distance`

获取服务器视距（以区块为单位）。

- **参数:** 无
- **返回值:**
  - `distance` (integer): 视距

#### `minecraft:serversettings/view_distance/set`

设置服务器视距。

- **参数:**
  - `distance` (integer, required): 新的视距
- **返回值:**
  - `distance` (integer): 设置后的新视距

#### `minecraft:serversettings/simulation_distance`

获取服务器模拟距离（以区块为单位）。

- **参数:** 无
- **返回值:**
  - `distance` (integer): 模拟距离

#### `minecraft:serversettings/simulation_distance/set`

设置服务器模拟距离。

- **参数:**
  - `distance` (integer, required): 新的模拟距离
- **返回值:**
  - `distance` (integer): 设置后的新模拟距离

#### `minecraft:serversettings/accept_transfers`

获取服务器是否接受来自其他服务器的玩家转移。

- **参数:** 无
- **返回值:**
  - `accepted` (boolean): 是否接受转移

#### `minecraft:serversettings/accept_transfers/set`

启用或禁用接受来自其他服务器的玩家转移。

- **参数:**
  - `accept` (boolean, required): 是否接受转移
- **返回值:**
  - `accepted` (boolean): 设置后的新状态

#### `minecraft:serversettings/status_heartbeat_interval`

获取服务器状态心跳包的发送间隔（秒）。

- **参数:** 无
- **返回值:**
  - `seconds` (integer): 心跳间隔

#### `minecraft:serversettings/status_heartbeat_interval/set`

设置服务器状态心跳包的发送间隔。

- **参数:**
  - `seconds` (integer, required): 新的心跳间隔
- **返回值:**
  - `seconds` (integer): 设置后的新间隔

#### `minecraft:serversettings/operator_user_permission_level`

获取执行操作员命令所需的权限等级。

- **参数:** 无
- **返回值:**
  - `level` (integer): 权限等级 (1-4)

#### `minecraft:serversettings/operator_user_permission_level/set`

设置执行操作员命令所需的权限等级。

- **参数:**
  - `level` (integer, required): 新的权限等级
- **返回值:**
  - `level` (integer): 设置后的新等级

#### `minecraft:serversettings/hide_online_players`

获取是否在状态查询中隐藏在线玩家信息。

- **参数:** 无
- **返回值:**
  - `hidden` (boolean): 是否隐藏

#### `minecraft:serversettings/hide_online_players/set`

启用或禁用在状态查询中隐藏在线玩家信息。

- **参数:**
  - `hide` (boolean, required): 是否隐藏
- **返回值:**
  - `hidden` (boolean): 设置后的新状态

#### `minecraft:serversettings/status_replies`

获取服务器是否响应连接状态请求。

- **参数:** 无
- **返回值:**
  - `enabled` (boolean): 是否响应

#### `minecraft:serversettings/status_replies/set`

启用或禁用服务器响应连接状态请求。

- **参数:**
  - `enable` (boolean, required): 是否响应
- **返回值:**
  - `enabled` (boolean): 设置后的新状态

#### `minecraft:serversettings/entity_broadcast_range`

获取实体广播范围（百分比）。

- **参数:** 无
- **返回值:**
  - `percentage_points` (integer): 广播范围百分比

#### `minecraft:serversettings/entity_broadcast_range/set`

设置实体广播范围（百分比）。

- **参数:**
  - `percentage_points` (integer, required): 新的广播范围百分比
- **返回值:**
  - `percentage_points` (integer): 设置后的新百分比

---

### 游戏规则

#### `minecraft:gamerules`

获取所有可用的游戏规则及其当前值。

- **参数:** 无
- **返回值:**
  - `gamerules` (array[TypedGameRule]): 游戏规则列表
    - `key` (string): 规则名称
    - `value` (string): 规则值
    - `type` (string): 值类型 ("boolean" 或 "integer")

#### `minecraft:gamerules/update`

更新指定游戏规则的值。

- **参数:**
  - `gamerule` (UntypedGameRule, required): 要更新的规则
    - `key` (string): 规则名称
    - `value` (string): 新的规则值
- **返回值:**
  - `gamerule` (TypedGameRule): 更新后的游戏规则对象

---

### 通知 (Notifications)

这些是服务器主动向客户端推送的事件。

- `notification:server/started`: 服务器已启动
- `notification:server/stopping`: 服务器正在关闭
- `notification:server/saving`: 服务器开始保存
- `notification:server/saved`: 服务器保存完成
- `notification:server/status`: 服务器状态心跳（包含 `status` 参数）
- `notification:players/joined`: 玩家加入（包含 `player` 参数）
- `notification:players/left`: 玩家离开（包含 `player` 参数）
- `notification:operators/added`: 玩家被授予 OP 权限（包含 `player` 参数）
- `notification:operators/removed`: 玩家被撤销 OP 权限（包含 `player` 参数）
- `notification:allowlist/added`: 玩家被加入允许列表（包含 `player` 参数）
- `notification:allowlist/removed`: 玩家被移出允许列表（包含 `player` 参数）
- `notification:ip_bans/added`: IP 被加入封禁列表（包含 `player` 参数）
- `notification:ip_bans/removed`: IP 被移出封禁列表（包含 `player` 参数，类型为 string）
- `notification:bans/added`: 玩家被加入封禁列表（包含 `player` 参数）
- `notification:bans/removed`: 玩家被移出封禁列表（包含 `player` 参数）
- `notification:gamerules/updated`: 游戏规则被更新（包含 `gamerule` 参数）

---

## 组件 (Components)

### 数据类型

#### `Player`

代表一个 Minecraft 玩家。

- `name` (string): 玩家名
- `id` (string): 玩家 UUID

#### `Operator`

代表一个操作员玩家。

- `player` (Player): 玩家信息
- `permissionLevel` (integer): 权限等级 (1-4)
- `bypassesPlayerLimit` (boolean): 是否绕过玩家数量上限

#### `UserBan`

代表一个用户封禁条目。

- `player` (Player): 被封禁的玩家
- `reason` (string): 封禁原因
- `expires` (string): 封禁过期时间
- `source` (string): 执行封禁的来源

#### `IpBan`

代表一个 IP 封禁条目。

- `ip` (string): 被封禁的 IP 地址
- `reason` (string): 封禁原因
- `expires` (string): 封禁过期时间
- `source` (string): 执行封禁的来源

#### `IncomingIpBan`

用于添加 IP 封禁的输入对象。

- `ip` (string): 要封禁的 IP
- `reason` (string): 封禁原因
- `expires` (string): 过期时间
- `source` (string): 来源
- `player` (Player): 关联的玩家（可选）

#### `ServerState`

代表服务器状态。

- `started` (boolean): 服务器是否运行
- `players` (array[Player]): 在线玩家
- `version` (Version): 服务器版本

#### `Version`

服务器版本信息。

- `name` (string): 版本名称
- `protocol` (integer): 协议版本

#### `Message`

消息内容。

- `literal` (string): 文本消息
- `translatable` (string): 可翻译的消息键
- `translatableParams` (array[string]): 可翻译消息的参数

#### `SystemMessage`

系统消息对象。

- `message` (Message): 消息内容
- `overlay` (boolean): 是否为屏幕中央的覆盖消息
- `receivingPlayers` (array[Player]): 接收者列表

#### `KickPlayer`

踢出玩家的输入对象。

- `players` (array[Player]): 被踢玩家
- `message` (Message): 踢出原因

#### `UntypedGameRule`

用于更新游戏规则的输入对象。

- `key` (string): 规则名
- `value` (string): 规则值

#### `TypedGameRule`

包含类型信息的游戏规则对象。

- `key` (string): 规则名
- `value` (string): 规则值
- `type` (string): 值类型 ("boolean", "integer")
