# deleteServerGroup


## 描述
删除虚拟服务器组

## 请求方式
DELETE

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/serverGroups/{serverGroupId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeCPSLBRegions）获取云物理服务器支持的地域|
|**serverGroupId**|String|True| |服务器组ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean|删除操作是否成功|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
