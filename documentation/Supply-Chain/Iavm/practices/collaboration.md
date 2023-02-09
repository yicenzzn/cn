
# 协同办公

协同办公组件助您提高工作效率，该镜像支持5个常用办公软件，分别是禅道项目管理工具、ONLYOFFICE文档工具、Nextcloud在线文件管理系统、MediaWiki 知识库、Superset数据可视化工具，一键全量安装和部署，便捷高效。


- 禅道Zentao 是优秀的研发项目管理工具，禅道细分需求、任务、缺陷和用例，完整覆盖了研发项目管理的核心流程
- MediaWiki 是“维基百科”网站开源的 Wiki 程序，适合用于构建百科、知识库、在线文档、个人笔记等应用
- Nextcloud 是一款用于自建企业云存储（私有网盘）的开源软件。支持 PC、IOS 和 Android 三个同步客户端，用户可以很方便地与服务器上存储的文件、日程安排、通讯录、书签等重要数据保持同步
- ONLYOFFICE Docs 是一个文档中间件，为文档管理软件提供Office格式的文档的在线预览与编辑，支持主流格式：docx、xlsx、pptx、odt、ods、odp、doc、xls、ppt、pdf、txt、rtf、html、epub、csv
- Superset 是一个开源的数据探查与可视化平台（曾用名 Panoramix、Caravel ），该工具在可视化、易用性和交互性上非常有特色，用户可以轻松对数据进行可视化分析


## 创建轻量云主机

访问轻量云主机[创建实例页](https://lavm-console.jdcloud.com/lavm/create)

选择协同办公镜像，以及套餐版本、时长等内容，进行下单创建轻量云主机实例

![图片名称](https://img1.jcloudcs.com/image/docs/8.png)


## 查看应用详情


支付完成后可以在控制台看到已购的轻量云主机，点击操作中的【查看】按钮


![图片名称](https://img1.jcloudcs.com/image/docs/1.png)


切换到应用管理页面查看应用的详细信息，获取WordPress初始化地址

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)



## 禅道

使用浏览器访问禅道（Zentao）地址，根据系统提示选择语言，点击“开始安装”

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)

接受License许可，安装进入环境检测页面，点击下一步

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)


系统初始化已经设置好数据库参数，点击下一步

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)


保存配置文件

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)

设置后台账号信息，请设置好并牢记账户和密码，然后“保存”

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)

根据您设置的用户和密码登录后台

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)

登录后台进行配置和使用

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)



## MediaWiki


使用浏览器访问MediaWiki地址

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)

点击【login in】,输入用户名和密码

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)


获取用户名和密码：在控制台直接点击【登录】或使用远程连接工具登录轻量云主机，输入命令cat /credentials/password.txt，获取用户名和密码

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)


进入MediaWiki后台，进行编辑使用

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)







## Nextcloud


使用浏览器访问Nextcloud地址，设置管理员账户和密码，点击安装


![图片名称](https://img1.jcloudcs.com/image/docs/3.png)


可以安装推荐的应用，或者取消推荐应用安装


![图片名称](https://img1.jcloudcs.com/image/docs/4.png)


关闭弹窗，查看后台内容

![图片名称](https://img1.jcloudcs.com/image/docs/5.png)


切换到文件页面，可以上传、下载您的文件

![图片名称](https://img1.jcloudcs.com/image/docs/5.png)


## Superset 


使用浏览器访问Superset地址

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)

在控制台直接点击【登录】或使用远程连接工具登录轻量云主机，输入命令cat /credentials/password.txt，获取用户名和密码

![图片名称](https://img1.jcloudcs.com/image/docs/2.png)









