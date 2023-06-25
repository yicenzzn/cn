# disassociateElasticIp


## 描述
解绑弹性公网IP


## 请求方式
PUT

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:disassociateElasticIp

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|
|**instanceId**|String|True| |分布式云物理服务器ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |由客户端生成，用于保证请求的幂等性，长度不能超过36个字符；<br/><br>如果多个请求使用了相同的clientToken，只会执行第一个请求，之后的请求直接返回第一个请求的结果<br/><br>|
|**elasticIpId**|String|True| |弹性公网IPId|
|**ipType**|String|False| |ipv4 or ipv6|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean|解绑结果|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
