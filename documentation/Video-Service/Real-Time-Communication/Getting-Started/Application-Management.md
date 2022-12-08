# 全局设置

针对全局可设置观看页、观看端、客户端、敏感词、登录页等功能设置；

## 观看皮肤设置

### 2.1.1、功能介绍

可以修改观看端页面设置

### 2.1.2、使用教程

第一步：全局设置页面【全局设置—观看页皮肤设置】
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

第二步：
1、选择皮肤风格：提供6款皮肤风格选择；
2、登录页面设置：默认关闭状态。开启后支持自定义设置PC登录页，关闭则使用系统默认图片样式；
开启后需上传对应背景图：
PC登录页背景图：建议图片尺寸为1920*700，有效内容范围在1100*700以内；图片支持jpg、jpeg、png格式，文件大小不超过2M
移动登录页背景图：建议尺寸为750*412；图片支持jpg、jpeg、png格式，文件大小不超过2M
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

## 2.2、观看端打赏设置

### 2.2.1、功能介绍

可以修改观看端打赏设置，包括现金打赏和道具打赏的相关设置。

### 2.2.2、使用教程

第一步：全局设置页面【全局设置—观看端打赏设置】

默认开启状态
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

第二步：修改设置

现金打赏： 开启后直播间应用全局的现金打赏设置
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

道具打赏： 开启后直播间应用全局的道具打赏设置
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)
第三步：保存

## 2.3、客户端设置

### 2.3.1、使用教程

可以修改客户端设置，包括自定义菜单、问卷设置和菜单设置。

### 2.3.2、使用教程

第一步：全局设置页面【全局设置—客户端设置】

自定义菜单、在线问卷导入默认关闭状态
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

第二步：修改设置

1) 自定义菜单：启用该功能后，直播客户端可以通过自定义菜单的方式加载用户自定义的网页，方便结合自身业务进行交互操作。

2) 问卷设置：在直播管理页面点击 “问卷设置”，启用该功能后，直播客户端可以通过接口请求的方式将用户问卷库中的问卷导入到客户端中使用，关于问卷设置的具体功能及使用方法，请参考：问卷接口开发指南。

3) 菜单设置：支持对客户端的互动功能进行自定义配置，关闭后客户端对应该功能隐藏。

## 2.4、敏感词设置

### 2.4.1、使用教程

可以修改敏感词设置，支持添加敏感词列表，敏感词库上限高达5万条。

### 2.4.2、使用教程

第一步：全局设置页面【全局设置—敏感词设置】
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

第二步：修改设置

1)全局设置中支持设置敏感词，支持手动单个添加及应用模板批量导入

2)已添加的敏感词支持删除操作，也可一键清空敏感词列表

3)支持按角色进行过滤，勾选后，该角色的聊天内容不进行敏感词过滤

4)敏感词处理机制支持删除与隐藏两种：

-设置删除，敏感词仅本人可见，聊天审核不展示敏感词消息

-设置隐藏，敏感词本人及管理者可见，聊天审核页面敏感词为隐藏状态，并有敏感词标识

-聊天导出中支持支持查看是否为敏感词以及聊天状态显示或隐藏

敏感词列表：
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

敏感词检测：
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

第三步：保存

## 2.5、自定义未登录页

### 2.5.1、使用教程

可以自定义未登录页。

### 2.5.2、使用教程

第一步：进入功能页面【通用设置-自定义未登录页】
![](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86-1.png)

第二步：修改设置

1)启用该功能后，若用户未登录则跳转到自定义的跳转页面地址，使用该功能必须使用自动登录，仅对学员观看端生效

第三步：保存






