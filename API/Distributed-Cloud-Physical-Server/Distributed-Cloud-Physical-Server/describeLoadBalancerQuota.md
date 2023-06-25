# describeLoadBalancerQuota


## 描述
查询负载均衡配额

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/describeLoadBalancerQuota

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeCPSLBRegions）获取云物理服务器支持的地域|

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
|**region**|String|地域|
|**userQuota**|Integer|用户配额|
|**usedQuota**|Integer|已用配额|
|**availableQuota**|Integer|可用配额|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
