# PrestaShop跨境电商平台

PrestaShop 是国外优秀的电子商务内容管理系统，操作简单，使用方便，支持600多个功能，5,000多个模块和主题的选购或内置，PrestaShop官方构建了一个非常完善、健康的商业化服务生态，是您搭建跨境电商独立平台的优选。


## 创建轻量云主机

访问轻量云主机[创建实例页](https://lavm-console.jdcloud.com/lavm/create)

选择PrestaShop镜像，以及套餐版本、时长等内容，进行下单创建轻量云主机实例

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop1.png)



## 查看应用详情

支付完成后可以在控制台看到已购的轻量云主机，点击操作中的【查看】按钮

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/1.png)


切换到应用管理页面查看应用的详细信息，获取PrestaShop首次访问地址

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/11.png)





## 初始化配置

使用浏览器访问管理员首次访问化地址


![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/12.png)


在控制台直接点击【登录】或使用远程连接工具登录轻量云主机，输入命令cat /credentials/password.txt，获取管理员账户和密码


![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/13.png)


登录后台后，您可以开始配置您的电商平台。

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/14.png)




## 管理员登录

后续管理员登录PrestaShop后台，您需要登录轻量云主机获取登录地址

输入命令cd /data/wwwroot/prestashop/data/prestashop， 获取admin文件夹名称

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/15.png)

管理员访问地址则例如是： http://域名/admin3110dsgyz 或 http://ip/admin3110dsgyz

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/16.png)


## 用户访问电商平台

使用浏览器访问PrestaShop前台展示地址（在应用详情页获取地址）

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop2.png)


## 设置成中文

登录PrestaShop管理员后台，选择International -> Localization， 选择China进行导入

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop3.png)


如果提示This functionality has been disabled， 请远程登录轻量云主机

输入命令 cd /var/lib/docker/volumes/prestashop_prestashop/_data/config

修改defines.inc.php 文件，修改 PS_MODE_DEMO 为false， 并在管理员后台重新选择China进行导入


![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop4.png)
![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop5.png)


点击右上角Your profile， 修改language 为中文

![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop6.png)


查看管理员后台显示中文


![图片名称](https://img1.jcloudcs.com/cn/image/iavm/%E5%9B%BE%E7%89%876/prestashop7.png)

