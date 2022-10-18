# DescribeSnapshotPolicies

## 描述

查询快照策略

## HTTP请求

POST <https://disk.jcloudcs.com/v1/regions/{regionId}/snapshotPolicies:describe>

## 请求参数

### 路径参数

| Param | Type | Required | Desc |
|---|---|---|---|
| regionId | string | Yes | 地域ID |

### 

```json
{
    "policyId": [string],
    "status": [int],
    "name": string,
    "order": orderItem,
    "pageNumber": int,
    "pageSize": int
}
```

* 详细描述

| Field | Type | Required | Desc |
|-----|------|-----|-----|
| policyId | [string] | No | 策略id，精确匹配 |
| status | [int] | No | 策略状态，精确匹配 |
| name | string  |  No  | 策略名称，模糊匹配 |
| order | [OrderItem](../model/OrderItem.md) | No | 排序字段，只支持 create_time和update_time |
| pageNumber | int | No | 页码；默认为1 |
| pageSize | int | No | 分页大小；默认为20；取值范围[10, 100] |


## 成功的响应

```json
{
    "result": {
        "totalCount": int,
        "policies": [snapshotPolicy]
    },
    "requestId": string
}
```

| Param | Type | Desc |
|---|---|---|
| totalCount | int | 总数量 |
| policies | [[SnapshotPolicy](../model/SnapshotPolicy.md)] | 策略列表 |


- 错误码

| Code | Status | Message |
|---|---|---|
| 400 | INVALID_ARGUMENT | Invalid region 'xxx' |
| 400 | INVALID_ARGUMENT | Malformed status 'xxx' |
| 500 | INTERNAL | Internal server error |
| 500 | UNKNOWN | Unknown server error |
| 503 | SERVICE UNAVAILABLE | Service unavailable |
