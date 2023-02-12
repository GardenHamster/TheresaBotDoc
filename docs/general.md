!> 注：除了更新cookie指令需要私发给机器人，其他指令都需要在群内发送

?> bot只会处理带有指令前缀的消息，你可以在botsettings.yml中修改该值，默认为`#`

?>  大部分指令名称并不是写死的，你完全可以在配置文件中进行修改

## #涩图
### 说明
从 `pixiv` 中搜索一张符合条件的色图，下载图片并发送到qq群中，响应速度取决于与pixiv连接的速度

### 指令
发送 `#涩图` 随机搜索一张涩图

发送 `#涩图 [自定义标签]` 根据标签随机搜索涩图

发送 `#涩图 [pid]` 根据pid获取涩图

### Gif

如果获取到的作品为动图时，会自动转换为gif，可以发送 `#涩图 [作品id]` 转换自己喜欢的动图

### 多标签
多个标签之间允许使用空格和逗号分割表示`并且`和`或者`的关系，逗号不区分中英符，比如：

标签 `萝莉 巨乳` 表示同时包含 `萝莉` 和 `巨乳` 这两个标签的涩图

标签 `白丝,黑丝` 表示只需要存在其中一个标签的涩图

标签 `萝莉,少女 白丝,黑丝` 表示包含`萝莉`或者`少女`，并且包含`白丝`或者`黑丝` 的涩图

### 示例
![image](/img/general/2023-02-12-14-41-20-265.jpg)

![image](/img/general/2023-02-12-15-25-02-149.jpg)


## #瑟图
### 说明
从 [lolicon api](https://api.lolicon.app) 中获取色图

### 指令
发送 `#瑟图` 随机搜索一张api中的涩图

发送 `#瑟图 [自定义标签]` 根据标签随机搜索涩图

### 多标签
功能同上面pixiv多标签搜索功能一致

### 示例
![image](/img/general/2023-02-12-16-08-57-032.jpg)


## #setu
### 说明
从 [lolisuki api](https://lolisuki.cc) 中获取涩图

### 指令
发送 `#setu` 随机搜索一张api中的涩图

发送 `#setu [自定义标签]` 根据标签随机搜索涩图

### 多标签
功能同上面pixiv多标签搜索功能一致

### 示例
![image](/img/general/2023-02-12-16-34-08-694.jpg)


## #本地涩图
### 说明
从本地获取涩图

### 指令
发送 `#本地涩图` 随机发送文件夹中的涩图

发送 `#本地涩图 [文件夹名称]` 随机发送指定文件夹中的涩图

### 示例
![image](/img/general/2023-02-12-17-25-23-928.jpg)


## #搜图
### 说明
调用 [saucenao](https://saucenao.com) 尝试搜索原图，如果存在匹配度较高的结果时，尝试获取下载并返回原图以及信息

如果saucenao中没有搜索到匹配结果是，可以选择是否使用ascii2d继续搜索，可以再配置文件中开启或关闭该功能

### 指令
发送 `#搜图` 根据提示进行操作

发送 `#搜图`+`一张或多张需要搜索图片` 

### 示例
![image](/img/general/2023-02-12-17-32-03-978.jpg)

![image](/img/general/2023-02-12-17-42-11-770.jpg)

## #菜单
### 说明
一个简陋的菜单功能，方便查询命令

### 示例
![image](/img/general/2023-02-12-01-49-34-249.jpg)

## #version
### 说明
获取当前版本号信息