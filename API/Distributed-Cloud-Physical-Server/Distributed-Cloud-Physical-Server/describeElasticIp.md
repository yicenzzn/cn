# describeElasticIp


## 描述
查询弹性公网IP详情

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/elasticIps/{elasticIpId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|
|**elasticIpId**|String|True| |弹性公网IPID|

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
|**elasticIp**|[ElasticIp](#elasticip)|弹性公网IP详细信息|
### <div id="ElasticIp">ElasticIp</div>
|名称|类型|描述|
|---|---|---|
|**region**|String|地域代码, 如cn-east-tz1|
|**elasticIpId**|String|弹性公网IPID|
|**elasticIp**|String|弹性公网IPv4|
|**targetIp**|String|对应绑定的资源(服务器/LB/NAT等等)的内网IPv4 或 别名IPv4|
|**eipv6**|String|弹性公网IPv6|
|**innerIpv6**|String|对应绑定的资源(服务器/LB/NAT等等)的内网IPv6 或 别名IPv6|
|**bandwidth**|Integer|带宽, 单位Mbps|
|**extraUplinkBandwidth**|Integer|额外上行带宽, 单位Mbps|
|**lineType**|String|链路类型|
|**status**|String|状态|
|**instanceType**|String|实例类型|
|**instanceId**|String|实例ID|
|**createTime**|String|创建时间|
|**bandwidthPackageId**|String|共享带宽 id|
|**charge**|[Charge](#charge)|计费信息|
### <div id="Charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
