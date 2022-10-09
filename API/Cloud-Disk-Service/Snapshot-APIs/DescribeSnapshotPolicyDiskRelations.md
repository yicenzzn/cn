# DescribeSnapshotPolicyDiskRelations
## 描述

查询快照策略与磁盘的绑定关系

## HTTP请求
POST <https://disk.jcloudcs.com/v1/regions/{regionId}/snapshotPolicyDiskRelations:describe>
## 请求参数

### 路径参数

| Param | Type | Required | Desc |
|---|---|---|---|
| regionId | string | Yes | 地域ID |

### 

```json
{
    "policyId": [string],
    "diskId": [string],
    "diskRegion": [string],
    "order": orderItem,
    "pageNumber": int,
    "pageSize": int
}
```

* 详细描述

| Field | Type | Required | Desc |
|-----|------|-----|-----|
| policyId | [string] | No | 策略ID，精确匹配 |
| diskId | [string] | No | 磁盘ID，精确匹配 |
| diskRegion | [string]  |  No  | 磁盘地域ID，精确匹配 |
| order | [OrderItem](../model/OrderItem.md) | No | 排序字段，只支持 create_time |
| pageNumber | int | No | 页码；默认为1 |
| pageSize | int | No | 分页大小；默认为20；取值范围[10, 100] |


## 成功的响应

```json
{
    "result": {
        "totalCount": int,
        "relationResults": [snapshotPolicyDiskRelation]
    },
    "requestId": string
}
```

| Param | Type | Desc |
|---|---|---|
| totalCount | int | 总数量 |
| policies | [[SnapshotPolicyDiskRelation](../model/SnapshotPolicyDiskRelation.md)] | 策略列表 |


- 错误码

| Code | Status | Message |
|---|---|---|
| 400 | INVALID_ARGUMENT | Invalid region 'xxx' |
| 500 | INTERNAL | Internal server error |
| 500 | UNKNOWN | Unknown server error |
| 503 | SERVICE UNAVAILABLE | Service unavailable |
