# associateElasticIp


## 描述

为合作云主机绑定合作弹性公网IP。

详细操作说明请参考帮助文档：合作[绑定弹性公网IP](https://docs.jdcloud.com/cn/coc-virtual-machines/associate-elastic-ip)

## 接口说明
- 该接口只支持在实例的主网卡的主内网IP上绑定合作弹性公网IP。
- 一台合作云主机的主网卡的主内网IP只能绑定一个合作弹性公网IP，若已绑定合作弹性公网IP，操作绑定会返回错误。
- 合作弹性公网IP所在的可用区需要与合作云主机的可用区保持一致，或者合作弹性公网IP是全可用区类型的，才允许绑定操作。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:associateElasticIp

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**elasticIpId**|String|True| |合作弹性公网IP的ID。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID。|


## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|FAILED_PRECONDITION|ElasticIp xx already in use|弹性公网IP已经绑定了其它实例。|
|**400**|FAILED_PRECONDITION|The instance and elasticIp 'xx' are in different azs.|弹性公网IP与云主机实例不在同一个可用区中。|
|**400**|FAILED_PRECONDITION|NetworkInterface already in use|云主机实例主网卡主内网IP已经绑定了公网IP。|
|**404**|NOT_FOUND|ElasticIpId xxx not found|弹性公网IP不存在。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:associateElasticIp
{
  "elasticIpId" : "fip-z1z1****ja"
}
```



## 返回示例

```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
