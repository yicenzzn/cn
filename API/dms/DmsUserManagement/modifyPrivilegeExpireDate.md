# modifyPrivilegeExpireDate


## 描述
修改权限到期时间

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:modifyPrivilegeExpireDate


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**idList**|Long[]|True| |授权实例记录对应的主键ID|
|**expireDate**|String|True| |授权过期时间(yyyy-MM-dd'T'HH:mm:ss.SSS'Z')|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
