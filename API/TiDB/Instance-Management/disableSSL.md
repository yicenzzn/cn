# disableSSL


## 描述
关闭 TiDB 和 MySQL 客户端之间的 SSL 连接功能。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/ssl:disableSSL

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
无


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**202**|OK|
