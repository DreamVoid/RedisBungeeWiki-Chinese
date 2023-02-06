# 插件

**RedisBungee**是先进的BungeeCord玩家同步系统。

下方（详细的）插件列表均支持RedisBungee。如果您的插件支持RedisBungee，请联系我并添加到此页。

## 自动集成

这些插件通常在RedisBungee环境下“开箱即用”

* [SimpleCommands](http://www.spigotmc.org/resources/simplecommands.289/): 自动集成RedisBungee数据。
* [BungeeTabListPlus](http://www.spigotmc.org/resources/bungeetablistplus.313/): 自动集成RedisBungee数据。
* [RedisMessage](http://www.spigotmc.org/resources/redismessage.9260/): 基于RedisBungee API开发。
* [UntamedChat](http://www.spigotmc.org/resources/untamedchat.2520/): 基于RedisBungee API开发。
* [Party and Friends Extended Edition for Bungeecord](https://www.spigotmc.org/resources/party-and-friends-extended-edition-for-bungeecord-example-server-hexagonmc-eu.10123/): 安装RedisBungee后立即启用接口支持。

## 手动集成

* [BungeeAdminTools](http://www.spigotmc.org/resources/bungee-admin-tools.444/): 您必须在配置文件中设置`redisSupport: true`。
* [BungeePlayerCounter](http://www.spigotmc.org/resources/bungeeplayercounter.269/): 您必须在配置文件中设置`datasource: redis`。
* [HolographicDisplays](http://dev.bukkit.org/bukkit-plugins/holographic-displays/):您必须在配置文件中设置`using-RedisBungee: true`。
* [UltimateVotes](http://www.spigotmc.org/resources/ultimatevotes-1-8-spigot-bungeecord.516/): 您必须在配置文件中设置`broadcastRedis: true`。
* 使用[MVdW placeholders](http://www.spigotmc.org/wiki/mvdw-placeholders/)的插件: 使用`{redisbungeecount}`占位符返回所有在线玩家，使用`{redisbungeecount@server}`占位符返回指定服务器的在线玩家。
* [UltimateFriends](http://www.spigotmc.org/resources/ultimate-friends.3964/): 您必须在`communication`部分设置`module: "redis"`。
* [UltimateVotes \(Bungee\)](http://www.spigotmc.org/resources/ultimatevotes-1-8-spigot-bungeecord-uuid.516/): 可以使用RedisBungee在服务器中运行命令。
* [BungeeTabComplete](http://www.spigotmc.org/resources/bungeetabcomplete.7328/): 需要在config.yml文件中启用配置。
* [GlobalTabList](http://www.spigotmc.org/resources/globaltablist.1117/): 您必须使用`{redis_count}`占位符。
* [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/): 您必须使用`%redisbungee_total%`和`%redisbungee_<server>`占位符，并设置`hooks.redisbungee: true`。
* [~~Global Perms~~](https://www.spigotmc.org/resources/global-perms.9932/) - _\[插件不再更新\]_
* [BungeeUtilsals](https://www.spigotmc.org/resources/bungeeutilisals.7865/): 需要在配置文件中设置`Use-RedisBungee: true`。
* [ReporterGUI](https://www.spigotmc.org/resources/reportergui.8596/)
* [PlayerBalancer](https://www.spigotmc.org/resources/10788/): 您必须在'settings'部分设置'redisbungee'为'true'

