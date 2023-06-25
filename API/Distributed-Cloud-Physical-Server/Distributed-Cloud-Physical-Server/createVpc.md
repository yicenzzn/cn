# createVpc


## 描述
创建私有网络

## 请求方式
PUT

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/vpcs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |由客户端生成，用于保证请求的幂等性，长度不能超过36个字符；<br/><br>如果多个请求使用了相同的clientToken，只会执行第一个请求，之后的请求直接返回第一个请求的结果<br/><br>|
|**vpcSpec**|[VpcSpec](#vpcspec)|True| |子网配置|

### <div id="VpcSpec">VpcSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**cidr**|String|True| |私有网络范围|
|**name**|String|True| |名称|
|**enableIpv6**|String|False|no|是否开通IPv6网关，取值范围：yes、no|
|**ipv6Cidr**|String|False| |ipv6 cidr|
|**description**|String|True| |描述|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**vpcId**|String|私有网络ID|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
