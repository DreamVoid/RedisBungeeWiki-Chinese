# API

**RedisBungee**是先进的BungeeCord玩家同步系统。

RedisBungee提供好用方便的集成方式。

## API稳定性

通常来说，API-breaking`（译注：破坏性API）`的更改仅在较新的版本中（例如0.2.5到0.3）可用。

## 推荐：RedisBungee Java API \(BungeeCord\)

集成RedisBungee的最佳方法是使用RedisBungee Java API，这种方法可用于BungeeCord插件。

有关此API的Javadoc可以在[md\_5的构建服务器](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html)获取。

### Maven

下列仓库包含了所有RedisBungee的构建：

[md\_5-snapshots](http://repo.md-5.net/content/repositories/snapshots/)

之后，您可以在您的插件项目中添加以下依赖项：

com.imaginarycode.minecraftRedisBungee0.3.6-SNAPSHOT provided

`译者注：有对原文进行小幅修改以便阅读。`

## 插件消息传递 \(Bukkit\)

在Bukkit服务端中，您可以通过使用插件消息传递API来集成RedisBungee的一些功能。RedisBungee会监听此API \(RedisBungee\)，并且传递的消息应均为 Data{Input,Output}Stream 格式。

### 接口例程

**发送消息**

```text
ByteArrayDataOutput out = ByteStreams.newDataOutput();
out.writeUTF("PlayerCount");
out.writeUTF("ALL");
player.sendPluginMessage(MyPlugin.getInstance(), "RedisBungee", out.toByteArray());
```

**解析ServerPlayers的返回内容**

```text
private Multiset<String> deserializeNoMembers(ByteArrayDataInput input) {
    int collectionSize = input.readInt();
    Multiset<String> multiset = HashMultiset.create();
    for (int i = 0; i < collectionSize; i++) {
        String in = input.readUTF();
        int cnt = input.readInt();
        multiset.setCount(in, cnt);
    }
    return multiset;
}

private Multimap<String, String> deserializeWithMembers(ByteArrayDataInput input) {
    int collectionSize = input.readInt();
    Multimap<String, String> multimap = HashMultimap.create();
    for (int i = 0; i < collectionSize; i++) {
        String in = input.readUTF();
        int cnt = input.readInt();
        for (int i1 = 0; i1 < cnt; i1++) {
            String in2 = input.readUTF();
            multimap.put(in, in2);
        }
    }
    return multimap;
}
```

**定义**

* 玩家
  * 名称或UUID \(Java或Mojang\)

**命令**

| 子通道 | 参数 | 响应 | 注释 |
| :--- | :--- | :--- | :--- |
| PlayerList | Server或ALL | 此命令将会返回使用逗号分隔的玩家列表\(参见注释\)。 | 由于存在一个Bug \(0.3.2已修复\)，第一个字符串将是**Players**而不是**PlayerList**。 |
| PlayerCount | Server或ALL | 此命令将会返回玩家人数。 |  |
| LastOnline | 参见`定义`部分 | 此命令返回后，由[getLastOnline\(\)](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html#getLastOnline%28java.util.UUID%29)接口输出一个长整数。 | `译者注：给出的链接提示403，因此无法得知此接口的具体用法。` |
| Proxy | _无_ | 此命令将会返回当前BungeeCord代理的ID | 于0.3.6版本加入 \(2015年6月29日\) |
| ServerPlayers | COUNT或PLAYERS | 此命令将会返回参数指定的类型，然后为排序后的multimap | 于0.3.6版本加入 \(2015年6月29日\)  `译者注：multimap实在不知道怎么翻译，应该是字符串一类` |

## Redis PubSub

RedisBungee支持Redis PubSub。将一个命令通过`redisbungee-allservers`从其中一个BungeeCord服务端发布到所有服务端执行，或通过`redisbungee-<SERVERID>`发布到指定的一个服务端执行。从RedisBungee 0.3版本开始，您也可以从单独的PubSub通道上监听PubSubMessageEvent事件。参见[registerPubSubChannels\(\)](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html#registerPubSubChannels\java.lang.String)、[unregisterPubSubChannels\(\)](https://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html#unregisterPubSubChannels%28java.lang.String)和[PubSubMessageEvent](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/events/PubSubMessageEvent.html)。`译者注：有对原文进行小幅修改以便阅读，但访问后均为403错误。`

如果您需要调用其中的命令，请确保来自`RedisBungeeCommandSender`！

## 不推荐：使用RedisBungee数据集进行`集成（Tinkering）`

尽管可以实现，但是这将在更待RedisBungee的数据模式后引发问题（这种问题很常见）一个很好的例子是从版本0.2.x升级到0.3.x，插件将开始存储UUID而非用户名。RedisBungee尽一切可能以人性化的方式从其他插件中隐藏自身内部的一些信息，由此您就可以轻松的进行后端更改。

`译者注：这里应该是作者在说升级到0.3版本可以避免在后台改东西的时候其他插件偷数据（不过一个BC端有什么数据好偷的呢）`

