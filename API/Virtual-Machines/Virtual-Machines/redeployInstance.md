# redeployInstance


## 描述

当云主机实例收到本地盘不可用、隔离坏本地盘等系统事件通知时，可调用该接口重新部署主机实例。


## 接口说明
- redeployInstance接口为异步调用接口，会迁移并重新部署实例；该操作将会清空本地数据盘的所有数据，请您谨慎操作。
- 必须是本地盘不可用、隔离坏本地盘的本地数据盘实例才可调用该接口，其余实例调用将会失败。
- 实例需要时运行中或者已停止状态。

## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:redeployInstance

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|cn-north-1| |地域ID。|
|**instanceId**|String|i-eumm****d6| |云主机ID。|

## 请求参数
无


## 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|**requestId**|String|a0633f72670e59f8c6db36b1ee257011|请求ID。|


## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:redeployInstance
```



## 返回示例

```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```


## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**400**|NOT_ISOLATED|Instance 'xx' not isolated.|云主机实例未隔离。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|
