# createInstance


## 描述
创建一个指定配置的kafka实例

## 请求方式
POST

## 请求地址
https://kafka.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |regionId 地域编码 https://docs.jdcloud.com/cn/jcs-for-kafka/restrictions|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instance**|[InstanceSpec](#instancespec)|True| |kafka实例的相关配置|
|**charge**|[ChargeSpec](#chargespec)|False| |计费信息的相关配置，只有prepaid_by_duration和postpaid_by_duration 2种计费模式|

### <div id="ChargeSpec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration。请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |包年包月付费单位或按配置/按用量计费模式定时转换为包年包月付费单位。仅chargeMode=prepaid_by_duration或chargeMode=postpaid_by_duration且autoChangeChargeMode=true时此参数有效。取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |包年包月付费时长或按配置/按用量计费模式定时转换为包年包月付费时长。chargeMode=prepaid_by_duration或chargeMode=postpaid_by_duration且autoChangeChargeMode=true时此参数有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| |自动续费。true为开通自动续费，false为不开通自动续费，默认为false，仅对包年包月资源有效。开通后，将以本次创建时的购买时长作为自动续费周期，自动续费周期可在续费管理功能中进行修改。|
|**autoChangeChargeMode**|Boolean|False| |计费模式定时转换，支持在某一时间内从按配置/按用量计费转换为包年包月计费。true为开通转换，false为不开通转换，默认false。且只有按配置/按用量计费支持开启。请参阅具体产品线帮助文档确认该产品线支持的计费类型转换。|
|**autoChangeChargeModeDate**|String|False| |计费模式定时转换日期，格式"yyyy-MM-dd" ,例"2022-12-18"。指定日期的0点开始执行转换 ,autoChangeChargeMode为true时必填。|
|**buyScenario**|String|False| |产品线统一活动凭证JSON字符串，需要BASE64编码，目前要求编码前格式为 {"activity":{"activityType":必填字段, "activityIdentifier":必填字段}}|
### <div id="InstanceSpec">InstanceSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**vpcId**|String|True| |私有网络vpcId|
|**subnetId**|String|True| |子网subnetId|
|**ipVersion**|String|False| |ipVersion，空(代表v4)或者v4&v6|
|**instanceVersion**|String|True| |kafka版本，[1.0.1,0.10.2,2.4,2.6.0]|
|**instanceName**|String|True| |kafka集群名称，不可为空，只支持大小写字母、数字、英文下划线或者中划线，以字母开头且不能超过32位|
|**azId**|String[]|True| |可用区 https://docs.jdcloud.com/cn/jcs-for-kafka/restrictions|
|**instanceClassSpec**|[InstanceClassSpec[]](#instanceclassspec)|True| |集群规格配置|
|**extension**|[ReqExtension](#reqextension)|False| |扩展配置|
|**resourceGroupId**|String|False| |资源组ID|
|**cpuArch**|String|False| |支持的cpu架构类型, 创建时选择，不选默认创建x86架构的实例|
### <div id="ReqExtension">ReqExtension</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**msgRetain**|Integer|False| |消息保留时长 [24～168] 小时。仅2.6.0版本生效|
|**externalServiceType**|String|False| |TPaaS环境kafka集群service对外访问方式。仅2.6.0版本生效|
|**tls**|Boolean|False| |tls是否打开，不传默认是false。仅2.6.0版本生效|
|**sasl**|Boolean|False| |sasl是否打开，不传默认是false。仅2.6.0版本生效|
|**autoCreateTopics**|Boolean|False| |是否开启自动创建topic选项。仅2.6.0版本生效|
|**defaultReplicas**|Integer|False| |打开自动创建topic时的默认副本数。仅2.6.0版本生效|
|**numPartitions**|Integer|False| |打开自动创建topic时的默认分区数。仅2.6.0版本生效|
|**note**|String|False| |实例的备注信息|
### <div id="InstanceClassSpec">InstanceClassSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**role**|String|True| |节点角色 [broker]|
|**nodeClassCode**|String|False| |节点规格代码 https://docs.jdcloud.com/cn/jcs-for-kafka/price-overview|
|**nodeCount**|Integer|False| |节点个数|
|**nodeDiskType**|String|False| |磁盘类型规格代码 https://docs.jdcloud.com/cn/jcs-for-kafka/price-overview|
|**nodeDiskGB**|Integer|False| |单节点磁盘大小单位GB|
|**instanceDiskGB**|Integer|False| |kafka实例磁盘大小单位GB|
|**throughputMB**|Integer|False| |kafka实例流量大小单位MB|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|结果|
|**requestId**|String|本次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|kafka实例编号|
|**buyId**|String|本次创建的订单号|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
