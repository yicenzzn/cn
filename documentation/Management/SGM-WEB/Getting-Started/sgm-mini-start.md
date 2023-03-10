# 为小程序快速安装探针

如果需要使用SGM-web来监控小程序，必须先通过CDN方式安装探针。本文介绍如何通过CDN方式为小程序安装SGM监控探针

## 前提条件

1.添加 https://lyra-m.jdcloud.com 到小程序白名单列表

2.已支持微信、支付宝、百度、京东、字节，开发框架 Taro3、Uni-app

## 操作步骤

### 接入方式

1.登录[SGM-web控制台](https://lyra-console.jdcloud.com)

2.在左侧菜单单击应用概览，在页面中点击添加应用

3.在基本设置tab中输入应用名称后自动生成接入方式。

4.小程序接入(应用类型选择（mp)

- 以文件方式安装探针：

1.获取sgm小程序版的采集脚本，放入小程序工程目录下的某个文件夹，如lib；

2.在app.js中的顶部添加如下代码,代码需放置在App({})之前

```
import SgmMpSDK from './lib/';
const sgmSdk = new SgmMpSDK({
   sid:'**********',
   pid:'**********',
});
```
5.点击保存应用，接入完成

通用配置项

|  参数   | 类型  | 描述 | 是否必选 | 默认值 |
|  ----  | ----  |----  |----  |----  |
| pid  | String | 应用唯一id，创建应用时自动生成 | 是 | 无 |
| sid  | String | 即站点id，加解密盐值，创建应用时自动生成 | 是 | 无 |
| src  | String | 探针地址 创建应用时自动生成  | 是 | 无 |
| crossorigin  | String | 开启跨域 | 是 | anonymous |
| name  | String | 探针类型标识 | 是 | SGMH5 |
| userKeys  | String | 用户ID取值变量，多个以逗号分隔 | 否 | 默认取Cookie中的pin,pt_pin,pwdt_id |
| initDomain  | String | 初始化配置通道 | 否 | https://lyra-m.jdcloud.com |



## 结果验证

部署完成后，访问[SGM-WEB控制台](https://lyra-console.jdcloud.com),点击左侧菜单应用概览，出现数据即接入完成（必须应用有访问才会产生数据）
## 卸载探针
1. app.js中删除如下代码：
```
import SgmMpSDK from './lib/';
const sgmSdk = new SgmMpSDK({
   sid:'**********',
   pid:'**********',
});
```
2. 删除SGM-WEB采集脚本

注意：

目前小程序探针已支持微信、支付宝、百度、京东、字节，开发框架 Taro3、Uni-app
## 常见问题

### 接入后如何验证接入成功了？

1. 首先访问页面，然后打开[SGM-WEB控制台](https://lyra-console.jdcloud.com)，点击左侧菜单应用概览，查看是否产生数据，若已经产生数据，则代表接入成功

### 接入成功后为什么控制台上没有监控数据？

1. 请确认应用是否有访问

2. 检查接入方式是否正确

3. 需检查是否对此小程序已支持

