# PolicyDiskRelationOpResult

绑定/解绑 策略 与 Disk 的操作结果类

```json
{
    "code": int,
        "message": string,
            "diskId": string,
    "diskRegion": string,
    "policyId":string,
    "op":int,
}
```

* 详细描述

| Field | Type | Desc |
|-----|-----|-----|
| code | int | 状态码 |
| message | string | 失败信息 |
| diskId | string | 磁盘ID |
| diskRegion | string | 磁盘地域ID |
| policyId | string | 策略ID |
| op | int | 1:绑定 2:解绑 |

* Code 含义

| Code | Desc |
|-----|-----|
| 0 | success |
| 1 | Internal server error |
| 2 | Policy not exist |
| 3 | Disk not exist |
| 4 | Op not allow |
