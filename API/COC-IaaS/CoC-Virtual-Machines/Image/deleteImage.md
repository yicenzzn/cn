# deleteImage


## 描述

删除一个私有镜像。

详细操作说明请参考帮助文档：[删除私有镜像](https://docs.jdcloud.com/cn/virtual-machines/delete-private-image)

## 接口说明
- 已共享的私有镜像在取消共享关系前不可以删除，如私有镜像已共享给其他用户，请取消共享后再进行删除。
- 只能操作私有镜像。


## 请求方式
DELETE

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/images/{imageId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**imageId**|String|True| |镜像ID。|

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
|**400**|FAILED_PRECONDITION|Can't delete this image|不允许删除非本用户下的私有镜像。|
|**400**|FAILED_PRECONDITION|Conflict with underlay image task 'xx'|镜像正在处理其它任务，请稍后再试。|
|**404**|NOT_FOUND|Image 'xx' not found|镜像不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
DELETE
```
```
/v1/regions/cn-north-1/images/img-m5s0****29
```

```

## 返回示例
```
{
    "requestId": "a0633f72670e59f8c6db36b1ee257011"
}
```
