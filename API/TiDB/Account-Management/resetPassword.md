# resetPassword


## 描述
重置 TiDB 实例的高权限账号的密码。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/accounts/{accountName}:resetPassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|
|**accountName**|String|True| |账号名|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**accountPassword**|String|True| |新密码|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
