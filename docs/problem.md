### 发送指令没有回应

* 优先检查`mcl`和`本插件`是否正常运行，检查命令行或者`Log目录`下是否有报错信息

* 检查配置`Permissions.AcceptGroups`中的群号有没有填写错误

* 检查修改配置文件后有没有重启本插件

* 检查有没有使用正确的前缀，例如`General.Prefix`中设置的是`#`号，那么对应的菜单指令为`#菜单`

* 检查指令是否发送到群里，而不是私聊机器人(大部分指令都是群聊指令)

* 查看mcl控制台中是否有回应消息，如果有代表可能被风控了，建议换一个账号重试

* 检查机器人是否在群里，是否被禁言

### 连接到mcl失败
```powershell
连接到mirai-console失败
System.Net.Http.HttpRequestException: 由于目标计算机积极拒绝，无法连接。 (127.0.0.1:8100)
 ---> System.Net.Sockets.SocketException (10061): 由于目标计算机积极拒绝，无法连接。
   at System.Net.Sockets.Socket.AwaitableSocketAsyncEventArgs.ThrowException(SocketError error, CancellationToken cancellationToken)
   at System.Net.Sockets.Socket.AwaitableSocketAsyncEventArgs.System.Threading.Tasks.Sources.IValueTaskSource.GetResult(Int16 token)
   at System.Net.Sockets.Socket.<ConnectAsync>g__WaitForConnectWithCancellation|277_0(AwaitableSocketAsyncEventArgs saea, ValueTask connectTask, CancellationToken cancellationToken)
   at System.Net.Http.HttpConnectionPool.ConnectToTcpHostAsync(String host, Int32 port, HttpRequestMessage initialRequest, Boolean async, CancellationToken cancellationToken)
   --- End of inner exception stack trace ---
```

- 检查mirai-http-api配置是否正确，[配置方法参考这里](miraiInstall?id=安装mirai-api-http插件)

- 检查mcl是否正常启动

- 检查bot账号是否正常登录

### 数据库连接失败
```bash
SqlSugar.SqlSugarException: 中文提示 :  连接数据库过程中发生错误，检查服务器是否正常连接字符串是否正确，实在找不到原因请先Google错误信息：The given key '0' was not present in the dictionary..
English Message : Connection open error . The given key '0' was not present in the dictionary.
   at SqlSugar.AdoProvider.GetDataReader(String sql, SugarParameter[] parameters)
   at SqlSugar.AdoProvider.SqlQuery[T,T2,T3,T4,T5,T6,T7](String sql, Object parameters)
   at SqlSugar.AdoProvider.SqlQuery[T](String sql, SugarParameter[] parameters)
   at SqlSugar.AdoProvider.SqlQuery[T](String sql, Object parameters)
   at SqlSugar.DbMaintenanceProvider.GetDataBaseList(SqlSugarClient db)
   at SqlSugar.MySqlDbMaintenance.CreateDatabase(String databaseName, String databaseDirectory)
   at SqlSugar.DbMaintenanceProvider.CreateDatabase(String databaseDirectory)
   at Theresa3rd_Bot.Dao.DBClient.CreateDB() in D:\project\Theresa3rd-Bot\Theresa3rd-Bot\Dao\DBClient.cs:line 17
```
```bash
System.Collections.Generic.KeyNotFoundException: The given key '25185' was not present in the dictionary.
   at SqlSugar.AdoProvider.GetDataReader(String sql, SugarParameter[] parameters)
   at SqlSugar.AdoProvider.SqlQuery[T,T2,T3,T4,T5,T6,T7](String sql, Object parameters)
   at SqlSugar.AdoProvider.SqlQuery[T](String sql, SugarParameter[] parameters)
   at SqlSugar.AdoProvider.SqlQuery[T](String sql, Object parameters)
   at SqlSugar.DbMaintenanceProvider.GetDataBaseList(SqlSugarClient db)
   at SqlSugar.MySqlDbMaintenance.CreateDatabase(String databaseName, String databaseDirectory)
   at SqlSugar.DbMaintenanceProvider.CreateDatabase(String databaseDirectory)
   at Theresa3rd_Bot.Dao.DBClient.CreateDB() in D:\project\Theresa3rd-Bot\Theresa3rd-Bot\Dao\DBClient.cs:line 17
```

- 检查appsettings.Production.json中数据库链接字符串完整，完整的链接字符串如下

```bash
Data Source=127.0.0.1;port=3306;Initial Catalog=theresa_bot;uid=root;pwd=123456;CharSet=utf8mb4;SslMode=None;
```

- 如果不是这个问题，百度一下关键的错误信息一般都能解决

### yml语法错误
*  遇到类似 `YamlDotNet.Core.YamlException` 情况需要重新检查 `botsetting.yml` 文件
  
*  对比源文件，检查文件中的键值是否被误改，或者设置了错误的值，或者值超出了上限等
  
*  如果属性值为空时需要保留一对单引号，不能直接删除

```bash
Unhandled exception. YamlDotNet.Core.YamlException: (Line: 18, Col: 30, Idx: 1361) - (Line: 18, Col: 49, Idx: 1380): Exception during deserialization
 ---> System.FormatException: Input string was not in a correct format.
   at System.Number.ThrowOverflowOrFormatException(ParsingStatus status, TypeCode type)
   at YamlDotNet.Serialization.NodeDeserializers.ScalarNodeDeserializer.DeserializeIntegerHelper(TypeCode typeCode, String value)
   at YamlDotNet.Serialization.NodeDeserializers.ScalarNodeDeserializer.YamlDotNet.Serialization.INodeDeserializer.Deserialize(IParser parser, Type expectedType, Func`3 nestedObjectDeserializer, Object& value)
   at YamlDotNet.Serialization.ValueDeserializers.NodeValueDeserializer.DeserializeValue(IParser parser, Type expectedType, SerializerState state, IValueDeserializer nestedObjectDeserializer)
   --- End of inner exception stack trace ---
   at YamlDotNet.Serialization.ValueDeserializers.NodeValueDeserializer.DeserializeValue(IParser parser, Type expectedType, SerializerState state, IValueDeserializer nestedObjectDeserializer)
   at YamlDotNet.Serialization.ValueDeserializers.AliasValueDeserializer.DeserializeValue(IParser parser, Type expectedType, SerializerState state, IValueDeserializer nestedObjectDeserializer)
   at YamlDotNet.Serialization.ValueDeserializers.NodeValueDeserializer.<>c__DisplayClass3_0.<DeserializeValue>b__0(IParser r, Type t)
```

### linux下报错
```
The remote certificate is invalid because of errors in the certificate chain: NotTimeValid
```
- 更新一下ca证书

```bash
yum update ca-certificates -y
```

### 日榜发送异常
```powershell
replyRankingInfo异常
System.ArgumentException: 调用http-api失败, 参数错误, 请到 https://github.com/Executor-Cheng/Mirai-CSharp/issues 下提交issue。
   at Mirai.CSharp.HttpApi.Extensions.ApiResponseExtensions.EnsureApiRespCode(JsonElement root)
   at Mirai.CSharp.HttpApi.Session.MiraiHttpSession.CommonSendMessageAsync(String action, Nullable`1 qqNumber, Nullable`1 groupNumber, IChatMessage[] chain, Nullable`1 quoteMsgId, CancellationToken token)
   at TheresaBot.MiraiHttpApi.Session.MiraiSession.SendGroupMergeMessageAsync(Int64 groupId, List`1 setuContents) in D:\project\Theresa3rd-Bot\Theresa3rd-Bot\TheresaBot.MiraiHttpApi\Session\MiraiSession.cs:line 93
   at TheresaBot.MiraiHttpApi.Session.MiraiSession.SendGroupSetuAsync(List`1 setuContents, Int64 groupId, Boolean sendMerge) in D:\project\Theresa3rd-Bot\Theresa3rd-Bot\TheresaBot.MiraiHttpApi\Session\MiraiSession.cs:line 118
   at TheresaBot.Main.Handler.PixivRankingHandler.replyRankingInfo(GroupCommand command, PixivRankingMode rankingMode, PixivRankingItem rankingItem) in D:\project\Theresa3rd-Bot\Theresa3rd-Bot\TheresaBot.Main\Handler\PixivRankingHandler.cs:line 196
```
- 出现这个异常需要将mirai-http-api.jar版本升级到`v2.9.1`及以上