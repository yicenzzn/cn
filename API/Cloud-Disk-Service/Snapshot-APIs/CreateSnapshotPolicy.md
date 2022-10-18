# CreateSnapshotPolicy

## 描述

创建快照策略

## HTTP请求

POST <https://disk.jcloudcs.com/v1/regions/{regionId}/snapshotPolicy>

## 请求参数

### 路径参数

| Param | Type | Required | Desc |
|---|---|---|---|
| regionId | string | Yes | 地域ID |

### 请求Body

模型 [here](../model/CreateSnapshotPolicyRequest.md)

## 成功的响应

```json
{
    "result": snapshotPolicy,
    "requestId": string
}
```
模型 [SnapshotPolicy](../model/SnapshotPolicy.md)

- 错误码

| Code | Status | Message |
|---|---|---|
| 400 | INVALID_ARGUMENT | Parameter name missing |
| 400 | INVALID_ARGUMENT | Parameter interval missing |
| 400 | INVALID_ARGUMENT | Parameter effective time missing |
| 400 | INVALID_ARGUMENT | Parameter status missing |
| 400 | INVALID_ARGUMENT | Parameter snapshotLifecycle missing |
| 400 | INVALID_ARGUMENT | Malformed name 'xxx' |
| 400 | INVALID_ARGUMENT | Malformed status 'xxx' |
| 400 | INVALID_ARGUMENT | Invalid region 'xxx' |
| 400 | INVALID_ARGUMENT | Invalid policy interval |
| 400 | INVALID_ARGUMENT | Invalid policy effectiveTime |
| 400 | INVALID_ARGUMENT | Invalid policy contactInfo sms/email |
| 400 | INVALID_ARGUMENT | Invalid policy contactInfo personId xxx |
| 400 | INVALID_ARGUMENT | Invalid policy contactInfo groupId xxx |
| 401 | UNAUTHENTICATED | Unauthenticated user pin 'xxx' |
| 429 | QUOTA_EXCEEDED | Snapshot policy quota limit exceeded |
| 500 | INTERNAL | Internal server error |
| 500 | UNKNOWN | Unknown server error |
| 503 | SERVICE UNAVAILABLE | Service unavailable |
