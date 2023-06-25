# createLoadBalancer


## 描述
创建负载均衡实例

## 请求方式
PUT

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/loadBalances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeCPSLBRegions）获取云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |由客户端生成，用于保证请求的幂等性，长度不能超过36个字符；<br/><br>如果多个请求使用了相同的clientToken，只会执行第一个请求，之后的请求直接返回第一个请求的结果<br/><br>|
|**loadBalancerSpec**|[LoadBalancerSpec](#loadbalancerspec)|True| |负载均衡配置|

### <div id="LoadBalancerSpec">LoadBalancerSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|False| |运营商|
|**netType**|String|True| |网络类型，取值public|
|**ipAddressType**|String|True| |负载均衡实例的IP版本，取值ipv4|
|**vpcId**|String|True| |私有网络ID|
|**name**|String|True| |名称|
|**description**|String|False| |描述|
|**applyElasticIp**|Boolean|True| |是否申请弹性公网Ip|
|**bandwidth**|Integer|True| |带宽|
|**extraUplinkBandwidth**|Integer|False| |额外上行带宽|
|**lbType**|String|False| |负载均衡类型：dlb；暂时仅支持dlb|
|**bmType**|String|False| |下属物理机类型，默认edcps|
|**charge**|[ChargeSpec](#chargespec)|True| |计费配置|
|**resourceTags**|[Tag[]](#tag)|False| |标签|
### <div id="Tag">Tag</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |标签键|
|**value**|String|True| |标签值|
### <div id="ChargeSpec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| |True=：OPEN——开通自动续费、False=CLOSE—— 不开通自动续费，默认为CLOSE|
|**buyScenario**|String|False| |产品线统一活动凭证JSON字符串，需要BASE64编码，目前要求编码前格式为 {"activity":{"activityType":必填字段, "activityIdentifier":必填字段}}|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**loadBalancerId**|String|负载均衡实例ID|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
