# describeSecondaryCidrs


## 描述
查询次要CIDR列表

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/secondaryCidrs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**subnetId**|String|True| |子网ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**secondaryCidrs**|[SecondaryCidr[]](#secondarycidr)| |
### <div id="SecondaryCidr">SecondaryCidr</div>
|名称|类型|描述|
|---|---|---|
|**secondaryCidrId**|String|次要cidr的ID|
|**cidr**|String|次要cidr|
|**region**|String|地域代码, 如cn-east-tz1|
|**az**|String|可用区, 如cn-east-tz1a|
|**subnetId**|String|子网ID|
|**name**|String|次要cidr名称|
|**vpcId**|String|私有网络Id|
|**vpcName**|String|私有网络名称|
|**vpcCidr**|String|私有网络cidr|
|**availableIpCount**|Integer|可用ip数量|
|**totalIpCount**|Integer|总ip数量|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
