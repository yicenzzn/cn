# stopInstance


## 描述

停止合作云主机实例。

详细操作说明请参考帮助文档：[停止实例](https://docs.jdcloud.com/cn/coc-virtual-machines/stop-instance)

## 接口说明
- 实例状态必须为运行 `running` 状态，同时实例没有正在进行中的任务时才可停止。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:stopInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID。|


## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|FAILED_PRECONDITION|Conflict with underlay task xx|云主机实例正在执行其它任务，请稍后再试。|
|**400**|FAILED_PRECONDITION|Invalid instance status xx|错误的云主机状态。|
|**400**|FAILED_PRECONDITION|keepCharging or stopCharging does not applied to dedicated host|专有宿主机中的实例不支持指定停机模式。|
|**400**|FAILED_PRECONDITION|stopCharging only applied to cloud system disk|停机停止计费模式只支持云盘系统盘的云主机。|
|**400**|FAILED_PRECONDITION|stopCharging only applied to postpaid by duration|停机停止计费模式只支持按配置计费的云主机。|
|**400**|FAILED_PRECONDITION|order not found|停机停止计费模式校验云主机计费单失败。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:stopInstance

```


## 返回示例
```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
