# ApplySnapshotPolicies

## 描述

绑定/解绑 策略 与 Disk 关系

## HTTP请求
POST <https://disk.jcloudcs.com/v1/regions/{regionId}/snapshotPolicies:apply>
## 请求参数

### 路径参数

| Param | Type | Required | Desc |
|---|---|---|---|
| regionId | string | Yes | 地域ID |

### 请求Body

```json
{
    "relations": [policyDiskRelationOp],
}
```

|  Field                       |  Type           |  Required     | Desc       |
|------------------------------|-----------------|-----------|------------|
|  relations            |  [[PolicyDiskRelationOp](../model/PolicyDiskRelationOp.md)]      |  Yes       | 解绑/绑定关系，长度[1, 100] |

## 成功的响应

```json
{
    "result": {
        "opResults": [policyDiskRelationOpResult]
    },
        "requestId": string
}
```
模型 [PolicyDiskRelationOpResult](../model/PolicyDiskRelationOpResult.md)

- 错误码

| Code | Status | Message |
|---|---|---|
| 400 | INVALID_ARGUMENT | Parameter diskId missing |
| 400 | INVALID_ARGUMENT | Parameter diskRegion missing |
| 400 | INVALID_ARGUMENT | Parameter policyId missing |
| 400 | INVALID_ARGUMENT | Parameter op missing |
| 400 | INVALID_ARGUMENT | Invalid relations length |
| 401 | UNAUTHENTICATED | Unauthenticated user pin 'xxx' |
| 500 | INTERNAL | Internal server error |
| 500 | UNKNOWN | Unknown server error |
| 503 | SERVICE UNAVAILABLE | Service unavailable |
