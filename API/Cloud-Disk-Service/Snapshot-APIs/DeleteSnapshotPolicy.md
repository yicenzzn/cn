# DeleteSnapshotPolicy
## 描述

删除快照策略

## HTTP请求

DELETE <https://disk.jcloudcs.com/v1/regions/{regionId}/snapshotPolicy/{policyId}>

## 请求参数

### 路径参数

| Param | Type | Required | Desc |
|---|---|---|---|
| regionId | string | Yes | 地域ID |
| policyId | string | Yes | 策略ID |

### 查询参数

无

## 成功的响应

```json
{
    "requestId": string
}
```

- 错误码

| Code | Status | Message |
|---|---|---|
| 400 | INVALID_ARGUMENT | Parameter id missing |
| 400 | INVALID_ARGUMENT | Invalid region 'xxx' |
| 404 | NOT_FOUND | Policy 'xxx' not found |
| 500 | INTERNAL | Internal server error |
| 500 | UNKNOWN | Unknown server error |
| 503 | SERVICE UNAVAILABLE | Service unavailable |
