# SnapshotPolicy

快照策略

```json
{
    "id": string,
    "name": string,
    "pin": string,
    "interval": int,
    "effectiveTime": string,
    "lastTriggerTime": string,
    "nextTriggerTime": string,
    "snapshotLifecycle": int,
    "contactInfo": ContactInfo,
    "createTime": string,
    "updateTime": string,
    "status": int,
    "diskCount": int
}
```

* 详细描述

| Param | Type | Desc |
|---|---|---|
| id | string | 策略id |
| name | string | 策略名称 |
| pin | string | 用户pin |
| interval | int | 策略执行间隔，单位:秒 |
| effectiveTime | string | 策略生效时间。格式`YYYY-MM-DDTHH:mm:ss+xx:xx`。如`2020-02-02T20:02:00+08:00`  |
| lastTriggerTime | string | 策略上次执行时间。格式`YYYY-MM-DDTHH:mm:ss+xx:xx`。如`2020-02-02T20:02:00+08:00`  |
| nextTriggerTime | string | 策略下次执行时间。格式`YYYY-MM-DDTHH:mm:ss+xx:xx`。如`2020-02-02T20:02:00+08:00`  |
| snapshotLifecycle | int | 快照保留时间。单位:秒。0: 永久保留 |
| contactInfo | [ContactInfo](ContactInfo.md) | 联系人信息 |
| createTime | string | 策略创建时间。格式`YYYY-MM-DDTHH:mm:ss+xx:xx`。如`2020-02-02T20:02:00+08:00` |
| updateTime | string | 策略更新时间。格式`YYYY-MM-DDTHH:mm:ss+xx:xx`。如`2020-02-02T20:02:00+08:00` |
| status | int | 策略状态 |
| diskCount | int | 策略绑定的disk数量 |
