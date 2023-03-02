### 指令没有回复
* 


### 数据库自动建表失败
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

### bot没有回复
* 检查配置文件中AcceptGroups中的群号有没有填写错误

* mcl控制台中有消息回应，但是群里没有消息出来，有可能是被风控了，建议换一个账号尝试

### bot只回复表情
* 只有#pixivcookie等更新cookie的指令需要私发给机器人以外，其他指令都要发送到群里面

* 有可能是你发送的指令不存在，或者使用了错误的指令前缀

* 修改了配置文件以后没有重启