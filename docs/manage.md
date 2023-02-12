!> 注：除了更新cookie指令需要私发给机器人，其他指令都需要在群内发送

?> bot只会处理带有指令前缀的消息，你可以在botsettings.yml中修改该值，默认为`#`

?>  大部分指令名称并不是写死的，你完全可以在配置文件中进行修改

## 禁止标签

### 说明

将一个标签加入到禁止搜索列表中，并且推送中不会再出现包含该标签的作品

匹配方式为部分一致，且大小写不敏感。当群不存在r18权限时，禁止该群搜索r18和r-18标签

![image](/img/manage/185851078-25151023-1359-405f-af53-c1371b39eb9d.png)

### 指令
发送 `#禁止标签 [关键词]` 禁止一个标签

发送 `#解禁标签 [关键词]` 解除一个标签

## 禁止成员

### 说明
将一个群员加入黑名单中，忽略其发送的所有指令

![image](/img/manage/185852450-b246798b-2a85-4eec-ac01-9f614f79eb50.png)

### 指令
发送 `#禁止成员 [qq号]` 拉黑一个成员

发送 `#解禁成员 [qq号]` 解除一个成员