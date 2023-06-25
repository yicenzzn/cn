# describeDeviceStock


## 描述
查询分布式云物理服务器库存

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/deviceStock

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**deviceType**|String|False| |实例类型，调用接口（describeDeviceTypes）获取实例类型|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**devicesStock**|[ResourceStock[]](#resourcestock)| |
### <div id="ResourceStock">ResourceStock</div>
|名称|类型|描述|
|---|---|---|
|**deviceType**|String|实例类型, 如 edcps.c.normal1|
|**region**|String|区域代码, 如 cn-east-tz1|
|**available**|Integer|可用库存|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
