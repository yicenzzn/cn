# createAccount


## 描述
创建数据库的高权限管理账号，用户可以使用客户端、应用程序等通过该账号和密码登录 TiDB 实例，然后通过SQL创建数据库和其他用户。一个数据库实例只能创建一个高权限账号。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountName**|String|True| |账号名|
|**accountPassword**|String|True| |密码|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
