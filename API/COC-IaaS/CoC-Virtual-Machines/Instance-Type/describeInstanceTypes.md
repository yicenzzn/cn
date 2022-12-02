# describeInstanceTypes


## 描述

查询实例规格列表。

详细操作说明请参考帮助文档：[实例规格类型](https://docs.jdcloud.com/cn/coc-virtual-machines/instance-type-family)

## 接口说明
- 调用该接口可查询全量实例规格信息。
- 可查询实例规格的CPU、内存大小、是否售卖等信息。
- 尽量使用过滤器查询关心的实例规格，并适当缓存这些信息。否则全量查询可能响应较慢。


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instanceTypes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**filters**|[Filter[]](#filter)|False| |<b>filters 中支持使用以下关键字进行过滤</b><br>`instanceTypes`: 实例规格，精确匹配，支持多个<br>`az`: 可用区，精确匹配，支持多个<br>`architecture`: CPU架构，精确匹配，支持单个，可选范围:x86_64或arm64<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instanceTypes**|[InstanceType[]](#instancetype)|实例规格详情列表。|
|**totalCount**|Integer|本次查询到的所有实例规格数量。|
### <div id="InstanceType">InstanceType</div>
|名称|类型|描述|
|---|---|---|
|**family**|String|实例规格族。|
|**instanceType**|String|实例规格。|
|**cpu**|Integer|cpu个数。|
|**memoryMB**|Integer|内存大小。|
|**state**|[InstanceTypeState[]](#instancetypestate)|实例规格售卖状态。已售罄的实例规格无法使用。|
|**architecture**|String|架构|
|**localDisks**|[FlavorDiskInfo](#flavordiskinfo)|本地盘配置。|
|**gpu**|[GpuInfo](#gpuinfo)|GPU配置。|
### <div id="GpuInfo">GpuInfo</div>
|名称|类型|描述|
|---|---|---|
|**model**|String|gpu model<br>|
|**number**|Integer|数量|
### <div id="FlavorDiskInfo">FlavorDiskInfo</div>
|名称|类型|描述|
|---|---|---|
|**diskType**|String|磁盘类型。<br>|
|**diskSizeGB**|Integer|磁盘大小。<br>|
|**count**|Integer|磁盘数量。|
### <div id="InstanceTypeState">InstanceTypeState</div>
|名称|类型|描述|
|---|---|---|
|**az**|String|可用区。|
|**inStock**|Boolean|售卖状态，`true`：可售卖、`false`：已售罄不可用。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET

```
/v1/regions/cn-north-1/instanceTypes?filters.1.name=instanceTypes&filters.1.values.1=g.n2.medium&filters.1.values.2=p.n1p4c.2xlarge
```


## 返回示例
```
{
    "requestId": "f9bcb6d3ed288538b74494e48af3c5fe", 
    "result": {
        "instanceTypes": [
            {
                "cpu": 1, 
                "family": "g.n", 
                "instanceType": "g.n2.medium", 
                "memoryMB": 4096, 
                "state": [
                    {
                        "az": "cn-north-1c", 
                        "inStock": true
                    }, 
                    {
                        "az": "cn-north-1a", 
                        "inStock": true
                    }, 
                    {
                        "az": "cn-north-1b", 
                        "inStock": true
                    }
                ]
            }, 
            {
                "cpu": 8, 
                "family": "p.n", 
                "instanceType": "p.n1p4c.2xlarge", 
                "memoryMB": 26624, 
                "state": [
                    {
                        "az": "cn-north-1c", 
                        "inStock": true
                    }, 
                    {
                        "az": "cn-north-1a", 
                        "inStock": false
                    }, 
                    {
                        "az": "cn-north-1b", 
                        "inStock": false
                    }
                ]
            }
        ], 
        "totalCount": 2
    }
}
```
