# 安装

**RedisBungee**是先进的BungeeCord玩家同步系统。

安装RedisBungee并连接到您的BungeeCord服务端非常容易。

## 要求

* 一个[Redis](http://redis.io/)服务器。
  * 如果您正在运行Debian 8或Ubuntu 14.04及以上，您可以使用root用户运行指令 apt-get install redis-server 快速安装。
  * 如果您正在运行CentOS 6，您需要下载并编译Redis的源代码。从0.3.8版本开始，RedisBungee不支持任何EPEL版本
  * 如果您正在运行CentOS 7, 您可以运行指令 yum install redis 快速安装。
  * 如果您的系统不支持直接安装Redis，或其版本不在2.6及以上，您需要到其[官方网站](http://redis.io/download)下载Redis。
  * （译者注）如果您正在运行Windows，您可以参阅[在Windows上安装Redis](https://www.redis.com.cn/redis-installation/)。
* 确保您用于运行BungeeCord服务端的所有服务器的系统时间同步。如果一个服务器和另一个服务器的系统时间差大于27秒，RedisBungee将会出现问题。配置NTP通常可用解决此问题。

## RedisBungee 0.3 及以上

* 下载RedisBungee插件文件并放置在BungeeCord服务端的插件文件夹。
* 启动一次BungeeCord服务端，然后关闭。
* 修改位于 plugins/RedisBungee/config.yml 的文件，调整各类配置尤其是“server-id”项和“redis-server”项。您可以参阅“配置”一节了解更多信息。
* 再次启动BungeeCord服务端，然后即可开始享受！

## RedisBungee 0.2.5 及以下

* 下载RedisBungee插件文件并放置在BungeeCord服务端的插件文件夹。
* 启动一次BungeeCord服务端，然后关闭。
* 修改位于 plugins/RedisBungee/config.yml 的文件，调整各类配置尤其是“server-id”项、“redis-server”项和“linked-servers”项。确保“linked-servers”项中包含您的所有BungeeCord服务端。
* 再次启动BungeeCord服务端，然后即可开始享受！

### 有关模块的注意事项

从BungeeCord版本`#787`开始，BungeeCord加入了一个模块系统。RedisBungee 0.3 将会在这些模块加载后自动加载，但这仅支持较新版本的BungeeCord。如果您必须使用0.2.x版本，您必须禁用cmd\_list和cmd\_find以让RedisBungee可以接管这些命令。请按下列步骤操作：

* 停止BungeeCord。
* 删除“modules/cmd\_list.jar”文件和“modules/cmd\_find.jar”文件。
* 编辑“modules.yml”文件并移除以下字段：“jenkins://cmd\_list”和“jenkins://cmd\_find”，然后保存文件。
* 重新启动BungeeCord。

