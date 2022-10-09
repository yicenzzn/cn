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
