# 用法

**RedisBungee**是先进的BungeeCord玩家同步系统。

本页介绍了如何配置和使用RedisBungee。

## 配置您的BungeeCord服务器

此步骤很大程度上取决于您如何配置BungeeCord。

### 我没有任何其他BungeeCord插件，或者其他插件不与玩家交互。

在此情况下，RedisBungee通常“开箱即用”，并且不需要任何额外配置。但是，请参阅下文中的Bukkit部分。

### 我有与玩家交互的BungeeCord插件。

在这种情况下，您将可能需要删除这些插件并调整BungeeCord设置，或者配置/更新您的此类插件以让RedisBungee正常工作。

### 那么我的Bukkit插件呢？

通常，依靠player-targeted信息执行操作的插件（比如连接信息）可以与RedisBungee正常工作。但是需要注意的是，依靠其他玩家和服务端支持的插件可能无法正常工作（比如消息传递）。

`译者注：本段包含一些不便翻译的单词，因此保留原文`

## 添加新的BungeeCord服务端

添加新的BungeeCord服务端非常容易：

* 配置新的BungeeCord端的配置与现有服务端相同
* 依照[安装](https://github.com/minecrafter/RedisBungee/wiki/Installation)指南进行配置，但请确保server-id唯一，并且redis-server项和其他BungeeCord端的配置一致。

不正确的执行以上步骤将**导致问题**！

