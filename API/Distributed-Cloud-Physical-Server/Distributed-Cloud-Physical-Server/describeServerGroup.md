# describeServerGroup


## 描述
查询虚拟服务器组

## 请求方式
GET

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
|**serverGroup**|[ServerGroup](#servergroup)|服务器组详细信息|
### <div id="ServerGroup">ServerGroup</div>
|名称|类型|描述|
|---|---|---|
|**loadBalancerId**|String|负载均衡ID|
|**serverGroupId**|String|虚拟服务器组ID|
|**name**|String|虚拟服务器组名称|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
