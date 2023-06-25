# 域名备案和解析


## 备案需求
域名需要备案完成，并且正确配置解析后，邮箱才能正常收发邮件。



## 步骤1： 域名备案

域名需要先完成备案后才能正常使用，如果还没有域名，请先[购买域名](https://net.jdcloud.com)。

京东云提供[备案服务](https://record-console.jdcloud.com)，助力您便捷完成备案。

购买正式的邮箱服务1年及以上的版本，可以提交工单获取授权码，一个正式版邮箱提供一个备案授权码。


![图片名称](https://img1.jcloudcs.com/image/docs/site-21.png)




## 步骤3: 对域名进行解析

通过域名访问某个邮箱的服务器，必须通过IP地址来实现，域名解析就是将域名重新转换为IP地址的过程。

访问[云解析DNS控制台](https://dns-console.jdcloud.com/list)，先添加域名。在域名列表选择刚添加的域名，点击操作中的解析。

![图片名称](https://img1.jcloudcs.com/image/docs/site0324-2.png)


点击添加解析。

![图片名称](https://img1.jcloudcs.com/image/docs/site0324-3.png)

在添加解析页面，进行解析记录配置。

- 记录类型：选择MX
- 记录值： 在邮箱控制台，查看详情页面进行获取
- 其它项：请见下图

![解析配置](https://img1.jcloudcs.com/image/step/8.png)


查看邮箱的解析地址。

在邮箱控制台，点击详情，查看需要配置的解析内容。

注意：邮箱专业版的MX解析地址和试用版不一样，需要根据版本选择不同的MX目标地址

![解析地址](https://img1.jcloudcs.com/image/step/9.png)







