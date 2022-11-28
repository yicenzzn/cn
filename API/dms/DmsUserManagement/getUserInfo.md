# getUserInfo


## 描述
获取用户信息

## 请求方式
GET

## 请求地址
https://dms.jdcloud-api.com/v1/management:getUserInfo


## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|[String](#result)|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**isMaster**|Boolean|是否是主账号|
|**username**|String|用户名|
|**pin**|String|用户pin|
|**masterPin**|String|用户主账号pin|
|**accountId**|Long|用户账号Id|
|**roleList**|String[]|用户角色信息|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
