# modifyInstance


## 描述
修改分布式云物理服务器部分信息，包括名称、描述

## 请求方式
POST

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|
|**instanceId**|String|True| |分布式云物理服务器ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |分布式云物理服务器名称|
|**description**|String|False| |分布式云物理服务器描述|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|分布式云物理服务器名称|
|**description**|String|分布式云物理服务器描述|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
