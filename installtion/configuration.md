# 配置

**RedisBungee**是先进的BungeeCord玩家同步系统。

RedisBungee允许您修改一些配置来指定Redis服务器和其他的一些行为.

### 例子

`译者注：以下是译者翻译后的配置文件`

```text
# RedisBungee 配置文件
# 请阅读指南: https://github.com/minecrafter/RedisBungee/wiki

# 您使用的Redis服务器
# 您可以在 http://redis.io/ 下载Redis
redis-server: 127.0.0.1
redis-port: 6379
# 可选: 如果您的Redis服务器需要身份验证，则您需要设置连接密钥
redis-password: ""
# 同时连接到Redis服务器的最大数量
# 默认值为8。正常情况下不应该修改此设置，
# 除非您的服务器由很多玩家或有一些效率低下的插件。
max-redis-connections: 8

# 当前BungeeCord的ID，必须唯一！
server-id: test1

# RedisBungee是否应注册并接管BungeeCord的一些自带命令
# 通常，您会需要RedisBungee接管自带命令，但是在某些情况下，
# 您或许会希望使用其他插件，此时可以设为false
#
# 如果您只想让玩家无法使用这些命令，默认的BungeeCord的权限系统
# 或您使用的权限组插件即可做到
# （译者注：参阅“命令”的“权限节点”一栏）
#
# 请注意，从787版本开始，RedisBungee接管的大部分命令以移动至模块（modules）
# 并且这些命令必须手动禁用以成功接管。
register-bungee-commands: true

# RedisBungee将不会对以下列出的IP地址修改BungeeCord返回的响应信息，
# 对于需要使用自动重新启动脚本的服务端很好用。
# 译者注：“BungeeCord返回的响应信息”指的是连接到当前BC端的人数等信息，RedisBungee会修改这个信息（比如人数）为整个服务器连接的人数
exempt-ip-addresses: []
```

## 配置

### redis-server、redis-port和redis-password

这些配置可以帮您指定连接到的Redis服务器。redis-server为服务器IP地址，redis-port为Redis绑定的端口号，redis-password为您设置的身份验证密钥（如果您设置了）。

### max-redis-connections

**不要修改此设置**。默认值通常可以正常工作，仅在建议修改时才修改此项。

### server-id

此配置用于RedisBungee标识当前BungeeCord端。这是非常重要的配置 - 不能有两个BungeeCord端使用相同的ID，因为这将会导致数据不一致问题。如果您一定要设置为相同的，那么仅当其中一个服务端离线20秒以上，另一个BungeeCord端的RedisBungee才会启用。

### register-bungee-commands

此配置允许您决定是否让RedisBungee注册并接管一些BungeeCord自带命令。其他命令（比如 /serverid、/serverids和/sendtoall）和基本的RedisBungee功能仍会正常工作。

### exempt-ip-addresses

如果发送给服务端的Ping请求的IP地址处于此列表内，则RedisBungee不会修改BungeeCord返回的响应信息。

`译者注：“BungeeCord返回的响应信息”指的是连接到当前BC端的人数等信息，RedisBungee会修改这个信息（比如人数）为整个服务器连接的人数`

