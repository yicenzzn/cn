# allocDedicatedHosts


## 描述
创建一台或多台指定机型的专有宿主机。<br>


详细操作说明请参考帮助文档：[创建专有宿主机](https://docs.jdcloud.com/cn/dedicated-host/create-dh)

## 接口说明
- 创建专有宿主机必须指定专有资源池。

## 请求方式
POST

## 请求地址
https://dh.jdcloud-api.com/v1/regions/{regionId}/dedicatedHosts

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|是|cn-north-1 |地域ID|

## 请求参数
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**dedicatedHostSpec**|[DedicatedHostSpec](allocDedicatedHosts#user-content-DedicatedHostSpec)|是| |描述专有宿主机配置<br>|
|**deployPolicy**|String|否|preferred|是否支持AZ内专有宿主机强制均衡，可选值：<br> preferred：（默认值）非强制<br>required：强制]<br>|
|**maxCount**|Integer|否|1|购买云主机的数量；取值范围：[1,100]，默认为1。<br>|
|**clientToken**|String|否 | |用于保证请求的幂等性。由客户端生成，长度不能超过64个字符。<br>|

### <div id="user-content-DedicatedHostSpec">DedicatedHostSpec</div>
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**dedicatedPoolId**|String|是 |pool-p2a****u0c |专有资源池ID，创建专有宿主机必须指定专有资源池ID|
|**az**|String|否| |专有宿主机所属的可用区，不传入该参数时可用区属性从专有宿主机池中继承；指定的可用区必须是对应专有宿主机池中设置的可用区的子集|
|**name**|String|是|dh-name |专有宿主机名称|
|**description**|String|否| |专有宿主机描述|
|**charge**|[ChargeSpec](allocDedicatedHosts#user-content-ChargeSpec)|否| |计费配置。<br>专有宿主机不支持按用量方式计费，默认为按配置计费。|
|**userTags**|[Tag[]](createInstances#user-content-3)|否| |自定义实例标签。以key-value键值对形式指定，最多支持10个标签。key不能以 "jrn:" 或“jdc-”开头，仅支持中文、大/小写英文、数字及如下符号：`\_.,:\/=+-@`。<br>|
|**resourceGroupId**|String| 否||资源组ID。|

### <div id="user-content-3">Tag</div>
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**key**|String|否|环境|标签key。长度不能超过127字符，不能以 `jrn:` 或 `jdc-` 开头，仅支持中文、大/小写英文、数字及如下符号：`\_.,:\/=+-@`。|
|**value**|String|否|测试|标签value。长度不能超过255字符，仅支持中文、大/小写英文、数字及如下符号：`\_.,:\/=+-@`。|

### <div id="user-content-ChargeSpec">ChargeSpec</div>
|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**chargeMode**|String|否 |postpaid_by_duration|计费模式，取值为：<br> prepaid_by_duration：预付费 <br> postpaid_by_duration：（默认值）按配置<br> 请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|否| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|否| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|否| |True：开通自动续费、False：（默认值）不开通自动续费|
|**buyScenario**|String|否| |产品线统一活动凭证JSON字符串，需要BASE64编码，目前要求编码前格式为 {"activity":{"activityType":必填字段, "activityIdentifier":必填字段}}|

## 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|**result**|[Result](allocDedicatedHosts#user-content-Result)| |响应结果 |
|**requestId**|String|c2hmmaan8w06w19qcdfuic4w03f7ft2d|请求ID |

### <div id="user-content-Result">Result</div>
|名称|类型|示例值|描述|
|---|---|---|---|
|**dedicatedHostIds**|String[]|["host-eumm****d6","host-y5nh****9w"] |专有宿主机ID列表 |

## 请求示例
POST

```
/v1/regions/cn-north-1/dedicatedHosts
{
  "dedicatedHostSpec":{
     "dedicatedPoolId":"pool-p2a****u0c",
     "name":"dh-name"
  },
  "maxCount":1
}
```



## 返回示例
```
{
    "result":{
    "dedicatedHostIds":[
      "host-eumm****d6",
      "host-y5nh****9w"
    ]
  },
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**429**|Quota exceeded|
|**500**|Internal server error|
|**503**|Service unavailable|
