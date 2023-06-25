# describeLoadBalancer


## 描述
查询负载均衡实例详情

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/loadBalances/{loadBalancerId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeCPSLBRegions）获取云物理服务器支持的地域|
|**loadBalancerId**|String|True| |负载均衡实例ID|

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
|**loadBalancer**|[LoadBalancer](#loadbalancer)|负载均衡实例详细信息|
### <div id="LoadBalancer">LoadBalancer</div>
|名称|类型|描述|
|---|---|---|
|**loadBalancerId**|String|负载均衡实例ID|
|**region**|String|地域，如cn-east-1|
|**ipAddressType**|String|IP版本，取值ipv4|
|**netType**|String|网络类型，取值public|
|**vpcId**|String|私有网络ID|
|**elasticIpId**|String|弹性公网IPID|
|**publicIp**|String|公网IP|
|**bandwidth**|Integer|带宽|
|**extraUplinkBandwidth**|Integer|EIP额外上行带宽|
|**status**|String|状态，取值active|inactive|
|**name**|String|名称|
|**description**|String|描述|
|**createTime**|String|创建时间|
|**charge**|[Charge](#charge)|计费配置|
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
