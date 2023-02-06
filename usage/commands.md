# 命令

**RedisBungee**是先进的BungeeCord玩家同步系统。

RedisBungee添加了几个实用的命令并接管一些BungeeCord的自带命令。

| 命令 | 权限节点 | 描述 |
| :--- | :--- | :--- |
| /glist | bungeecord.command.list | /glist本身只会返回玩家数量，/glist showall则可以显示所有玩家。 |
| /find | bungeecord.command.find | /find没有任何实质性的改动。 |
| /lastseen | redisbungee.command.lastseen | /lastseen允许您查看某个玩家的最后在线时间。 |
| /ip | redisbungee.command.ip | /ip允许您查看指定在线玩家的IP地址。 |
| /sendtoall | redisbungee.command.sendtoall | /sendtoall允许您发送命令到所有BungeeCord端并以控制台身份执行。 |
| /serverid | redisbungee.command.serverid | /serverid返回您当前连接到的RedisBungee端。 |
| /serverids | redisbungee.command.serverids | /serverids返回服务器中所有已注册`（已连接）`的服务器ID。 |
| /pproxy | redisbungee.command.pproxy | /pproxy返回指定玩家连接到的服务器的ID。 |
| /plist | redisbungee.command.plist | /plist和/glist相似，但是可以被当前连接到代理端的玩家运行。此命令允许一个附加参数，即/plist、/plist atl1和/plist atl1 showall都对atl1有效。 |

