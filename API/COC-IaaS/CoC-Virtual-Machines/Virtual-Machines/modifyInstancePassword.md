# modifyInstancePassword


## 描述

修改合作云主机密码。

详细操作说明请参考帮助文档：[重置密码](https://docs.jdcloud.com/cn/coc-virtual-machines/reset-password)

## 接口说明
- 实例没有正在进行中的任务时才可操作。
- 重置密码后，需要重启实例后生效。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyInstancePassword

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**password**|String|True| |实例密码。<br>可用于SSH登录和VNC登录。<br>长度为8\~30个字符，必须同时包含大、小写英文字母、数字和特殊符号中的三类字符。特殊符号包括：\(\)\~!@#$%^&\*\_-+=\|{}\[ ]:";'<>,.?/，`。<br>更多密码输入要求请参见 [公共参数规范](https://docs.jdcloud.com/virtual-machines/api/general_parameters)。<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID。|


## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|INVALID_ARGUMENT|Invalid password|密码不符合规范。|
|**400**|FAILED_PRECONDITION|Conflict with underlay task 'xx'|云主机实例正在执行其它任务，请稍后再试。|
|**400**|FAILED_PRECONDITION|Invalid instance status 'xx'|错误的云主机状态。|
|**404**|NOT_FOUND|System disk not found|云主机没有挂载系统盘。|
|**404**|FAILED_PRECONDITION|Invalid system disk mount state|云主机系统盘挂载状态异常。|
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

```
/v1/regions/cn-north-1/instances/i-eumm****d6:modifyInstancePassword
{
    "password" : "Instance@359"
}
```


## 返回示例
```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
