# modifyInstanceAttribute


## 描述

修改一台合作云主机的属性。

详细操作说明请参考帮助文档[修改实例名称](https://docs.jdcloud.com/cn/coc-virtual-machines/modify-instance-name)

## 接口说明
- 当前仅支持修改实例的名称。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstanceAttribute

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |实例名称。长度为2\~128个字符，只允许中文、数字、大小写字母、英文下划线（\_）、连字符（-）及点（.），不能以（.）作为首尾。<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID。|


## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|INVALID_ARGUMENT|There are no modifiable properties in the parameter|未指定任何可修改的属性。|
|**400**|INVALID_ARGUMENT|Add metadata key-value count more than xx pairs.|metadata数量超出规定范围。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:modifyInstanceAttribute
{
    "name":"test",
    "description" : "test"
}
```


## 返回示例
```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
