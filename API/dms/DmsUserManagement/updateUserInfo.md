# updateUserInfo


## 描述
更新用户信息

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:updateUserInfo


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pin**|String|True| |被更新用户的pin信息|
|**phone**|String|False| |用户手机号码|
|**email**|String|False| |用户邮箱|
|**roleList**|String[]|True| |用户角色列表信息|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
