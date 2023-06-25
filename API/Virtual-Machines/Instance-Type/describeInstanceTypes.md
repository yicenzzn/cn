# describeInstanceTypes


## 描述

查询实例规格列表。

详细操作说明请参考帮助文档：[实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)

## 接口说明
- 调用该接口可查询全量实例规格信息。包括规格的CPU、内存、可绑定的弹性网卡数量、可挂载的云硬盘数量，以及在不同可用区下的售卖情况。
- GPU类型规格 或 存储优化型规格可查询 GPU卡型号及数量，本地盘容量、类型及数量。
- 建议尽量使用过滤器查询关心的实例规格，并适当缓存这些信息，否则全量查询可能响应较慢。


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instanceTypes

|名称|类型|是否必需|示例值|描述|
|---|---|---|---|---|
|**regionId**|String|是|cn-north-1|地域ID。|

## 请求参数
|名称|类型|是否必选|示例值|描述|
|---|---|---|---|---|
|**serviceName**|String|否|vm|产品线类型，可选值：<br>`vm`（默认值）：云主机<br>`nc`：原生容器|
|**chargeMode**|String|否|prepaid_by_duration|计费类型，可选值：<br>`prepaid_by_duration`（默认值）：包年包月<br>`postpaid_by_duration`：按配置<br>`postpaid_by_spot`：抢占式
|**filters**|[Filter[]](describeInstanceTypes#user-content-filter)|否| |<b>filters 中支持使用以下关键字进行过滤</b><br>`instanceTypes`: 实例规格，精确匹配，支持多个<br>`az`: 可用区，精确匹配，支持多个<br>`architecture`：CPU架构，精确匹配，支持单个，可选值：`x86_64`或`arm64`|

### <div id="user-content-filter">Filter</div>
|名称|类型|是否必选|示例值|描述|
|---|---|---|---|---|
|**name**|String|是|instanceTypes |过滤条件的名称|
|**operator**|String|否| eq|过滤条件的操作符，默认eq|
|**values**|String[]|是| g.n2.xlarge|过滤条件的值|

## 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|**result**|[Result](describeInstanceTypes#user-content-result)| |响应结果。|
|**requestId**|String|c2hmmaan8w06w19qcdfuic4w03f7ft2d|请求ID。|

### <div id="user-content-result">Result</div>
|名称|类型|示例值|描述|
|---|---|---|---|
|**instanceTypes**|[InstanceType[]](describeInstanceTypes#user-content-instancetype)| |实例规格详情列表。|
|**specificInstanceTypes**|[InstanceType[]](describeInstanceTypes#instancetype)| |参数已废弃，无须关注。|
|**totalCount**|Integer| |本次查询到的所有实例规格数量。|

### <div id="user-content-instancetype">InstanceType</div>
|名称|类型|示例值|描述|
|---|---|---|---|
|**family**|String|g.n|实例规格族。|
|**generation**|Integer|2|实例规格代数。|
|**instanceType**|String|g.n2.xlarge|实例规格。|
|**cpu**|Integer|4|vcpu个数。|
|**memoryMB**|Integer|8192|内存大小，单位MiB。|
|**nicLimit**|Integer|4|支持绑定的弹性网卡数量，包括主网卡。|
|**cloudDiskCountLimit**|Integer|8|支持挂载的云硬盘数量，包括云盘系统盘。|
|**desc**|String| |实例规格描述。|
|**state**|[InstanceTypeState[]](describeInstanceTypes#user-content-instancetypestate)| |实例规格售卖状态。已售罄的实例规格无法使用。|
|**gpu**|[Gpu](describeInstanceTypes#user-content-gpu)| |GPU配置，针对GPU类型的实例规格有效。|
|**localDisks**|[LocalDisk[]](describeInstanceTypes#user-content-localdisk)| |本地数据盘配置（缓存盘），针对GPU类型、或本地存储型的实例规格有效。|

### <div id="user-content-localdisk">LocalDisk</div>
|名称|类型|示例值|描述|
|---|---|---|---|
|**diskType**|String|HDD|磁盘类型。可能值：`NVMe SSD、HDD`。|
|**diskSizeGB**|Integer|1117|磁盘大小，单位GiB。|

### <div id="user-content-gpu">Gpu</div>
|名称|类型|示例值|描述|
|---|---|---|---|
|**model**|String|Nvidia Tesla P40|GPU卡型号。|
|**number**|Integer|4|GPU卡数量。|

### <div id="user-content-instancetypestate">InstanceTypeState</div>
|名称|类型|示例值|描述|
|---|---|---|---|
|**az**|String|cn-north-1b|可用区。|
|**inStock**|Boolean|True|售卖状态，`true`：可售卖、`false`：已售罄不可用。|


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
                "architecture": "x86_64", 
                "cloudDiskCountLimit": 8, 
                "cpu": 1, 
                "desc": "", 
                "family": "g.n", 
                "generation": 2, 
                "instanceType": "g.n2.medium", 
                "memoryMB": 4096, 
                "nicLimit": 2, 
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
                "architecture": "x86_64",
                "cloudDiskCountLimit": 8, 
                "cpu": 8, 
                "desc": "", 
                "family": "p.n", 
                "generation": 1, 
                "gpu": {
                    "model": "Nvidia Tesla P4", 
                    "number": 1
                }, 
                "instanceType": "p.n1p4c.2xlarge", 
                "memoryMB": 26624, 
                "nicLimit": 4, 
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

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|
