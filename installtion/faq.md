# 常见问题

**RedisBungee**是先进的BungeeCord玩家同步系统。

## 什么是RedisBungee？

RedisBungee是一个玩家同步系统。适用于大型、专业的Minecraft服务器。

### 但是这到底是什么呢？

RedisBungee:

* **可以**通过简单的API方便的管理您拥有的所有BungeeCord服务器的所有玩家
* **可以**将您的所有服务器连接到一起。
* **不能**重新实现BungeeCord的API，因为这很麻烦。
* **不能**自动将您的玩家分布到不同的服务器。
* **不能**同步您的BungeeCord配置。
* **不能**替代BungeeCord的force hosts。

## 什么是Redis？

引用自[官方介绍](http://redis.io/topics/introduction):

```text
Redis是一个以BSD协议开源的、高级的键值存储。通常被称为“数据结构处理服务器”，因为其包含字符串、哈希值、列表和集合。
```

## 我能在Windows使用RedisBungee吗？

是。据我所知，一些RedisBungee的用户正在使用Windows，并且可以正常工作，但是RedisBungee并不建议这样。您必须使用Redis的Microsoft Open Technology端口绑定端口。您也可以使用运行Linux的专用服务器运行Redis服务器，然后在Windows上运行BungeeCord服务端。

## RedisBungee支持的最低的Redis版本是多少？

RedisBungee（从0.3.8起）需要Redis服务器的版本为2.6及以上，因为需要[Lua脚本支持](http://redis.io/commands/eval)。欲获得最佳性能，请使用Redis 2.8.10及以上。

## 当我尝试关闭BungeeCord时，RedisBungee输出了很多错误！

请更新BungeeCord到[\#1025](http://ci.md-5.net/job/BungeeCord/1025/)及以上，即可修复此问题。

`译者注：建议始终使用最新版本的BungeeCord。`

## RedisBungee无法连接到我的Redis服务器！

* 请确认您的Redis服务器正常运行。
* 请确保您的Redis版本在2.6及以上。
* 请确保您可以从域名连接到您的Redis服务器。
* 如果您在Redis配置中设置了身份验证密钥，则还需要在RedisBungee的配置文件中的redis-password项设置密钥。
* 尝试使用最新版本的RedisBungee。

## Redis Sentinel可以同时和RedisBungee一起运行吗？

RedisBungee当前并不支持Redis Sentinel，因为目前对此的需求不大。将来有可能会支持。

`译者注：鉴于作者已经停更，想要支持还是自己改代码吧。`

## 我已经安装RedisBungee，但是无法与另一个BungeeCord端的玩家交互！

首先，请查看此页面了解支持RedisBungee的插件。如果您的插件支持RedisBungee但并不工作，请联系插件作者。

如果您安装的插件不在列表中，则说明它们可能不支持RedisBungee。请记住，**RedisBungee不是魔法**。它不会立即显示服务器上的所有玩家，因为这会消耗大量本不必消耗的资源。请联系作者（或其他开发者）以让他们使用RedisBungee的API。如果您无法这样做，请与我联系（你必须给点小费）。

## 我已经安装RedisBungee，但是遇到了方法和类相关的错误！

除非您愿意自己修改插件源代码或为插件付费，否则请不要想着支持旧版本的BungeeCord或Spigot。我们几乎没有想要支持旧版本的Minecraft，因为我们的插件主要基于Minecraft的最新版本开发。

## 我更新了BungeeCord，然后接收到AccessControlExceptions错误

更新RedisBungee以解决此问题。

## 我已经安装RedisBungee但是我的TAB列表并未同步！

RedisBungee本身并不能同步TAB列表，因为这不是本插件应该做的。您可以考虑使用诸如[BungeeTabListPlus](http://www.spigotmc.org/resources/bungeetablistplus.313/)等插件。

## 我的其中一个BungeeCord服务器没有显示正确的服务器数量，或玩家列表是错误的。

* 请确保您的配置文件无误。
* 请确保您可以连接到Redis服务器。
* 请确保所有BungeeCord服务端已经启动。
* **请确保运行BungeeCord的服务器的系统时间是同步的**。如果BungeeCord服务端所在服务器在30秒内没有更新特定的时间戳，RedisBungee将自动移出此BungeeCord服务端。我已经收集了一些有关Linux发行版本的说明。
* 请确保所有BungeeCord服务端运行相同版本的RedisBungee。CI构建版特别容易出现此情况，因为经常对master分支进行实验性改动。`（译者注：现在CI貌似都不复存在了）`
* 请确保您正在使用最新版本的RedisBungee。

如果以上步骤均无法解决问题，请尝试寻求支持服务。`（译者注：请知悉，本插件已经不再维护）`

## RedisBungee正在刷屏！

`译者注：acting up不知道怎么翻译，根据语境，“刷屏”是最好的翻译`

* 您的插件可能向RedisBungee发送了过多的请求。**首先**尝试移除所有能向RedisBungee发送请求的插件。
* 尝试在redis.conf文件中设置maxclients为0。需要重新启动Redis服务器以应用更改。

## 我需要让Redis能够访问外部网络的BungeeCord服务端！

### 在继续下面的操作前，请阅读[http://redis.io/topics/security](http://redis.io/topics/security)。

将Redis配置文件的“IP绑定”值设为0.0.0.0或者直接注释掉。如果您在意安全问题，还可以更改Redis服务器绑定的端口。

您有两种选择：

* 限制对Redis服务器的访问
  * IPTables
    * `iptables -A INPUT -s 127.0.0.1 -p tcp --dport 6379 -j ACCEPT`
    * `iptables -A INPUT -s <BC端IP地址> -p tcp --dport 6379 -j ACCEPT`
    * `iptables -A INPUT -p tcp --dport 6379 -j DROP`
  * 其他方法
    * 您也可以使用加密连接，推荐使用[spiped](https://www.tarsnap.com/spiped.html)。
    * 设置密码
      * 在您的Redis配置文件中设置身份验证密码。另请注意，密码是使用明文不加密发送的（您可以使用SSL，但是这会造成性能损失，仅建议小型服务器使用）。您还需要在RedisBungee配置中设置redis-password为您设置的密码

现在，您可以重新启动Redis服务器和BungeeCord服务端。

## 我想将功能X添加到RedisBungee！

RedisBungee有意限制其作用范围。通常，如果其涉及到当前版本的BungeeCord不可用的功能，除非有可用例子，否则添加的可能性极低。

## 源代码在哪里浏览？

本插件在[GitHub](https://github.com/thechunknetwork/RedisBungee)开源并使用[Unlicense](http://unlicense.org/)协议（在2015年6月9日之前，我使用WTFPL协议）。但是，我更希望您可以提交一个PR。

## 您拥有Maven仓库吗？

md\_5-snapshots [http://repo.md-5.net/content/repositories/snapshots/](http://repo.md-5.net/content/repositories/snapshots/)

`译者注：有对原文进行小幅修改以便阅读。`

