# describeKeypairs


## 描述

批量查询密钥对。

详细操作说明请参考帮助文档：[密钥概述](https://docs.jdcloud.com/cn/virtual-machines/keypair-overview)


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/keypairs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeKeypairs#Result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**keypairs**|[Keypair[]](describeKeypairs#Keypair)|密钥信息列表。|
|**totalCount**|Number|本次查询可匹配到的总记录数，使用者需要结合 `pageNumber` 和 `pageSize` 计算是否可以继续分页。|
### <div id="Keypair">Keypair</div>
|名称|类型|描述|
|---|---|---|
|**keyName**|String|密钥对名称。|
|**keyFingerprint**|String|密钥对的指纹，根据 `RFC4716` 定义的公钥指纹格式，采用 `MD5` 信息摘要算法。|
|**createTime**|String|密钥创建时间。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|OUT_OF_RANGE|PageSize out of range|分页大小超出规定范围。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET
```
```
/v1/regions/cn-north-1/keypairs
```

```

## 返回示例
```
{
    "requestId": "aeb6716d70a99a8f1c5abc35eddb1830", 
    "result": {
        "keypairs": [
            {
                "createTime": "2020-12-08 16:52:02", 
                "keyFingerprint": "25:65:12:a9:2a:d8:03:97:a4:59:ce:3c:fe:00:aa:7c", 
                "keyName": "test"
            }
        ], 
        "totalCount": 1
    }
}
```
