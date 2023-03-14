# 为H5应用快速安装探针

如果需要使用SGM-WEB来监控H5应用，必须先通过CDN方式安装探针。本文介绍如何通过CDN方式为Web应用安装SGM前端监控探针

## 操作步骤

### 接入方式

1.登录[SGM-WEB控制台](https://lyra-console.jdcloud.com)

2.在左侧菜单单击应用概览，在页面中点击添加应用

3.在基本设置tab中输入应用名称后自动生成接入方式。

(1)前端探针接入(应用类型选择h5或pc)

- 以CDN方式安装探针：
  <br/>首先输入应用名称，会自动生成下方接入代码，将其粘贴到要接入 SGM 的页面中，保存应用
   ```
   <script crossorigin src="https://****.com/sgm-web-****.js" name="SGMH5" sid="********" pid="*********"></script>
   ```
**说明**
* 强烈建议将粘贴代码做为index.html页面中第一个资源引用，以便 SGM 采集的数据更及时，更准确。

完整的HTML示例：
```
<html>
<head>
  <title>Test page in http://test.com</title>
</head>
<body>
    <script crossorigin src="https://****.com/sgm-web-****.js" name="SGMH5" sid="****" pid="****"></script>
    <div id="app"></div>
</body>
</html>
```
4.点击保存应用，完成接入

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

1. 删除在页面中引入的sgm相关标签
2. 重新打包部署


## 常见问题

### 接入后如何验证接入成功了？

1. 首先访问页面，然后打开[SGM-WEB控制台](https://lyra-console.jdcloud.com)，点击左侧菜单应用概览，查看是否产生数据，若已经产生数据，则代表接入成功

### 接入成功后为什么控制台上没有监控数据？

1. 请确认应用是否有访问

2. 检查接入方式是否正确

