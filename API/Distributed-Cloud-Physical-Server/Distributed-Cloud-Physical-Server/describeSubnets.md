# describeSubnets


## 描述
查询子网列表

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/subnets

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码；默认为1|
|**pageSize**|Integer|False|20|分页大小；默认为20；取值范围[20, 100]|
|**az**|String|False| |可用区，精确匹配|
|**name**|String|False| |子网名称|
|**vpcId**|String|False| |私有网络ID，精确匹配|
|**filters**|[Filter[]](#filter)|False| |subnetId - 子网ID，精确匹配，支持多个<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**subnets**|[Subnet[]](#subnet)| |
|**pageNumber**|Integer|页码；默认为1|
|**pageSize**|Integer|分页大小；默认为20；取值范围[20, 100]|
|**totalCount**|Integer|查询结果总数|
### <div id="Subnet">Subnet</div>
|名称|类型|描述|
|---|---|---|
|**region**|String|地域代码, 如cn-east-tz1|
|**az**|String|可用区, 如cn-east-tz1a|
|**subnetId**|String|子网ID|
|**name**|String|子网名称|
|**cidr**|String|子网CIDR|
|**secondaryCidrName**|String|子网次要CIDR名称|
|**secondaryCidr**|String|子网次要CIDR|
|**secondaryCidrId**|String|子网次要CIDR ID|
|**vpcId**|String|私有网络Id|
|**vpcName**|String|私有网络名称|
|**vpcCidr**|String|私有网络IPv4 CIDR|
|**availableIpCount**|Integer|可用ip数量|
|**totalIpCount**|Integer|总ip数量|
|**usedIpv6IpCount**|Integer|已用IPv6地址数量|
|**totalIpv6IpCount**|String|总IPv6地址数量|
|**networkType**|String|网络类型|
|**ipv6Cidr**|String|私有网络IPv6 CIDR|
|**isIpv6Open**|Integer|是否开启Ipv6，1：开启，0：未开启|
|**description**|String|描述|
|**createTime**|String|创建时间|
|**vpcIpv6Cidr**|String|私有网络IPv6 CIDR|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
