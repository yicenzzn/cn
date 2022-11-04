# attachDisk


## 描述

为一台合作云主机挂载合作云硬盘。

详细操作说明请参考帮助文档：[挂载合作云硬盘](https://docs.jdcloud.com/cn/coc-virtual-machines/attach-cloud-disk)

## 接口说明
- 合作云主机和合作云硬盘都没有正在进行中的的任务时才可以操作。
- 合作云主机状态必须是 `running` 或 `stopped` 状态。操作系统盘时必须先停止实例。
- 待挂载的合作云硬盘与合作云主机实例必须在同一个可用区下。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:attachDisk

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskId**|String|True| |合作云硬盘ID。|
|**deviceName**|String|False| |磁盘逻辑挂载点。系统盘：必须指定并且只能是vda。数据盘：取值范围：[vdb~vdbm]|


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
|**400**|FAILED_PRECONDITION|Duplicated system disk|云主机实例中已存在系统盘。|
|**400**|FAILED_PRECONDITION|DataDisks out of range|云主机实例挂载的云硬盘已达到实例规格的限制上限。|
|**400**|FAILED_PRECONDITION|DeviceName 'xx' has been used|指定的盘符在云主机实例中已经存在。|
|**400**|FAILED_PRECONDITION|Disk 'xx' already attached|云硬盘已经挂载在当前实例中。|
|**400**|FAILED_PRECONDITION|Disk busy in 'xx'|云硬盘正在执行其它任务，请稍后再试。|
|**400**|FAILED_PRECONDITION|The system disk does not support shared disk|系统盘不支持使用共享型云硬盘。|
|**400**|FAILED_PRECONDITION|Disk attachment limit exceeded|共享型云硬盘、或非共享型云盘已经达到可挂载实例的上限。|
|**400**|FAILED_PRECONDITION|Invalid disk status 'xx'|云硬盘状态错误。|
|**400**|FAILED_PRECONDITION|The instance and disk are not in the same az|云硬盘与云主机不在同一可用区中。|
|**400**|FAILED_PRECONDITION|System disk size constraints|云硬盘作为系统盘超过规定大小。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**404**|NOT_FOUND|Disk 'xx' not found.|云硬盘不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:attachDisk
{
    "diskId" : "vol-u8r2****c1",
    "deviceName" : "vdb"
}
```


## 返回示例

```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
