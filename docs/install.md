## 安装数据库
数据库为mysql，需要自行安装，或者可以购买云数据库，推荐安装 [v8.0.31](https://dev.mysql.com/get/Downloads/MySQLInstaller/mysql-installer-community-8.0.31.0.msi) 及以上，[点击查看新手教程](mysqlInstall.md)

## 安装mcl
参照 [mirai-console-loader](https://github.com/iTXTech/mirai-console-loader) 文档安装mcl，并为其配置 [mirai-api-http](https://github.com/project-mirai/mirai-api-http) 插件，然后为mcl配置bot账号密码，[点击查看新手教程](miraiInstall.md)

## 启动mcl
运行 `mcl.cmd` 启动mcl控制台，正常启动结果如下
```bash
2023-02-12 02:35:59 I/main: Auto-login 123456789, protocol: ANDROID_PHONE, heartbeatStrategy: STAT_HB
2023-02-12 02:35:59 I/Bot.123456789: Loaded account secrets from local cache.
2023-02-12 02:35:59 I/Bot.123456789: Saved account secrets to local cache for fast login.
2023-02-12 02:35:59 I/Bot.123456789: Login successful.
2023-02-12 02:36:00 V/Bot.123456789: Event: BotOnlineEvent(bot=Bot(123456789))
2023-02-12 02:36:00 I/Bot.123456789: Bot login successful.
2023-02-12 02:36:00 I/main: mirai-console started successfully.
```

## 下载插件
从 [releases](https://github.com/GardenHamster/Theresa3rd-Bot/releases) 中下载最新版本的压缩包，然后解压到某个英文路径下，并不需要放到mcl目录下

## 连接mcl
修改根目录下的配置文件appsettings.Production.json，使项目可以连接上mcl
```json
{
  "Mirai": {                        //mirai-api-http配置在mcl目录config/net.mamoe.mirai-api-http/setting.yml里面
    "host": "127.0.0.1",            //mcl主机ip
    "port": "8100",                 //mirai-api-http配置的port
    "authKey": "theresa3rd",        //mirai-api-http中配置的verifyKey
    "botQQ": "123456789"            //mcl中登录的QQ号
  },
  "Database": {
    "ConnectionString": "Data Source=127.0.0.1;port=3306;Initial Catalog=theresa_bot;uid=root;pwd=123456;CharSet=utf8mb4;SslMode=None;"    //mysql数据库链接，确保能连上数据库以后，然后改成自己的
  }
}
```

## 修改配置
根据自己的需要修改根目录下的配置文件`botsettings.yml`，修改完成后需要重新启动，配置说明[点击这里](https://github.com/GardenHamster/Theresa3rd-Bot/blob/main/botsetting.md)

!> 注：各版本之间的`botsettings.yml`可能会有较大差异，升级版本后请注意对比并修改该文件

## Linux下部署
1. 签名密钥并添加 Microsoft 包存储库

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

2. 安装ASP.NET Core 6.0 运行时

```bash
sudo yum install aspnetcore-runtime-6.0
```

3. 切换到Theresa3rd-Bot.dll所在目录下，运行Theresa3rd-Bot.dll

```bash
nohup dotnet Theresa3rd-Bot.dll --launch-profile Production --urls http://0.0.0.0:8088
```

4. 升级ca证书

```bash
yum update ca-certificates -y
```

## Windows下部署
1. 下载并安装 [ASP.NET Core Runtime 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)，推荐下载页面中的 [Hosting Bundle](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-6.0.8-windows-hosting-bundle-installer)

2. 启动 powershell 并将路径切换到Theresa3rd-Bot.dll所在目录下

3. 运行Theresa3rd-Bot.dll，这里的端口可以随意填，但是不要填mcl的端口

```bash
dotnet TheresaBot.MiraiHttpApi.dll --launch-profile Production --urls http://0.0.0.0:8088
```

4. 可以在桌面创建一个 powershell.ps1 脚本方便一键启动

```bash
$host.ui.RawUI.WindowTitle="Theresa3rd-Bot"
cd C:\Theresa3rd-Bot
dotnet TheresaBot.MiraiHttpApi.dll --launch-profile Production --urls http://0.0.0.0:8088
```

### 正常运行结果如下
```bash
2023-02-12 03:13:31,548 INFO  ConsoleLog - 日志配置完毕...
2023-02-12 03:13:31,725 INFO  ConsoleLog - 配置文件读取完毕...
2023-02-12 03:13:31,742 INFO  ConsoleLog - 尝试连接到mirai-console...
2023-02-12 03:13:32,209 INFO  ConsoleLog - 已成功连接到mirai-console...
2023-02-12 03:13:32,339 INFO  ConsoleLog - 开始初始化数据库...
2023-02-12 03:13:33,267 INFO  ConsoleLog - 数据库初始化完毕...
2023-02-12 03:13:33,327 INFO  ConsoleLog - 网站cookie加载完成...
2023-02-12 03:13:33,344 INFO  ConsoleLog - 订阅任务加载完成...
2023-02-12 03:13:33,353 INFO  ConsoleLog - 加载禁止标签完毕
2023-02-12 03:13:33,354 INFO  ConsoleLog - 加载黑名单完毕
2023-02-12 03:13:33,356 INFO  ConsoleLog - pixiv用户订阅任务启动完毕...
2023-02-12 03:13:33,356 INFO  ConsoleLog - pixiv标签订阅任务启动完毕...
2023-02-12 03:13:33,356 INFO  ConsoleLog - 米游社订阅任务启动完毕...
2023-02-12 03:13:33,489 INFO  ConsoleLog - Cookie检查定时器启动完毕...
2023-02-12 03:13:33,492 INFO  ConsoleLog - 定时清理任务初始化完毕...
2023-02-12 03:13:33,492 INFO  ConsoleLog - Theresa3rd-Bot启动完毕，版本：v0.8.0
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: https://localhost:5001
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5000
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: D:\project\Theresa3rd-Bot\Theresa3rd-Bot\TheresaBot.MiraiHttpApi
```


## 开启VPN
需要一个可以访问外网的环境，本人使用的是[自由鲸](https://www.freewhale.us/auth/register?code=sQAT)(原心阶)，邀请码为sQAT

从0.4.0版本开始加入了免代理，通过修改SNI的方式访问pixiv，然后通过pixiv.re代理下载图片。

你可以在`botsettings.yml`中开启该功能，但不建议在有梯子的情况下启用它。

最后在你运行这个插件的机器上登录 [pixiv](https://www.pixiv.net)，确保机器可以正常访问P站

## 配置 pixiv cookie
pc端登录P站后按下`F12`，然后在P站中随意搜索一个标签，在网络中找到如下请求。

这里以搜索Hololive为例，获取的cookie中必须包含PHPSESSID。

然后使用 #pixivcookie [获取到的cookie] 格式私聊发送给机器人，和机器人必须为好友

![image](/img/install/177747559-168c1377-db4a-49f0-869f-78749f80707e.png)

![image](/img/install/177748449-02f59d79-a0bc-4475-80f6-40f0c56e06a6.png)

## 配置 saucenao cookie
在未设置cookie的情况下，Saucenao搜索限制为每个ip每日搜索50次，每30秒搜索3次，在使用频率较高的情况下，建议设置cookie

pc端打开[https://saucenao.com](https://saucenao.com)，点击右下角的Account然后登录saucenao

按下F12，然后在控制台/Console中输入`document.cookie`

然后使用 #saucenaocookie [获取到的cookie] 格式私聊发送给机器人，与机器人必须为好友

![image](/img/install/177758500-94720035-c11a-4689-bb91-eca1ac95ce7e.png)

![image](/img/install/177758915-69de1308-d934-407f-a945-17252124c969.png)

## 更新版本的步骤

1. 关掉正在运行的 powershell脚本

2. 替换掉除了以下几个以外的文件

* `botsettings.yml`
* `appsettings.json`
* `appsettings.Production.json`

3. 如果botsettings.yml有更新，则需要修改该文件到最新版本

4. 重启插件

## 其他

### pixiv图片代理
如果在qq中打开原图连接时出现感叹号，或者打不开原图链接时，[可以参考这里配置一个自己的图片代理](imgProxy.md)，然后修改相关配置