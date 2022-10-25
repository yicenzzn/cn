# PolicyDiskRelationOp

绑定/解绑 策略 与 Disk 的操作类

```json
{
    "diskId": string,
    "diskRegion": string,
    "policyId":string,
    "op":int,
}
```

* 详细描述

| Field | Type | Required | Desc |
|-----|-----|-----|-----|
| diskId | string | Yes | 磁盘ID |
| diskRegion | string | Yes | 磁盘地域ID |
| policyId |  string  | Yes | 策略ID |
| op | int | Yes | 1:绑定 2:解绑 |
