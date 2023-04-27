# detachDisk


## 描述

为一台合作云主机缷载合作云硬盘

详细操作说明请参考帮助文档：[缷载合作云硬盘](https://docs.jdcloud.com/cn/coc-virtual-machines/detach-cloud-disk)

## 接口说明
- 合作云主机和合作云硬盘都没有正在进行中的的任务时才可以操作。
- 合作云主机状态必须是 `running` 或 `stopped` 状态。操作系统盘时必须先停止实例。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:detachDisk

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |合作云硬盘ID。|


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
|**400**|FAILED_PRECONDITION|Please stop the instance first|需要先停止实例。|
|**400**|FAILED_PRECONDITION|Disk busy in 'xx'|云硬盘正在执行其它任务，请稍后再试。|
|**400**|FAILED_PRECONDITION|Invalid disk status 'xx'|云硬盘状态错误。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**404**|NOT_FOUND|Disk 'xx' not found.|云硬盘不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:detachDisk
{
    "diskId" : "vol-u8r2****c1"
}
```


## 返回示例
```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
