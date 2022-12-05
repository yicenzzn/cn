# checkInstance


## 描述
校验用户是否有实例权限

## 请求方式
GET

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:check

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |实例id|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**error**|[Error](#error)| |
|**requestId**|[String](#error)|请求id|

### <div id="error">Error</div>
|名称|类型|描述|
|---|---|---|
|**code**|Integer|0，成功；-1，失败。|
|**message**|String|错误消息。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
