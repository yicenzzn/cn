# modifyVpc


## 描述
修改私有网络


## 请求方式
POST

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/vpcs/{vpcId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|
|**vpcId**|String|True| |私有网络ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |名称|
|**description**|String|False| |描述|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**vpc**|[Vpc](#vpc)|私有网络详细信息|
### <div id="Vpc">Vpc</div>
|名称|类型|描述|
|---|---|---|
|**region**|String|地域代码, 如cn-east-tz1|
|**vpcId**|String|私有网络ID|
|**name**|String|私有网络名称|
|**cidr**|String|私有网络CIDR|
|**ipv6Cidr**|String|私有网络IPv6 CIDR|
|**isIpv6Open**|Integer|是否开启Ipv6，1：开启，0：未开启|
|**description**|String|描述|
|**createTime**|String|创建时间|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
