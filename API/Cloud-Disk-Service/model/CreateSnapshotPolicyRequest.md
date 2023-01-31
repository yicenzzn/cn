# CreateSnapshotPolicyRequest

创建快照策略请求参数

```json
{
    "name": string,
    "interval":int,
    "effectiveTime":string,
    "snapshotLifecycle":int,
    "contactInfo":ContactInfo,
    "status":int
}
```

* 详细描述

|  Field                       |  Type           |  Required     | Desc       |
|------------------------------|-----------------|-----------|------------|
|  name            |  string      |  Yes       | 策略名称 |
|  interval		 |  int  |  Yes        | 策略执行周期，单位:秒，不小于12小时 |
|  effectiveTime |  string  |  Yes  | 策略生效时间，格式`YYYY-MM-DDTHH:mm:ss+xx:xx`。如`2020-02-02T20:02:00+08:00` |
|  snapshotLifecycle		 |  int  |  Yes        | 快照保留时间，单位:秒，0:表示不删除 |
|  contactInfo		 |  [contactInfo](ContactInfo.md)  |  No        | 联系人信息 |
|  status		 |  int  |  Yes        | 策略状态。1:启用 2:禁用 |
