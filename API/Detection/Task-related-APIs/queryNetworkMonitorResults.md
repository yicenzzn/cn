# queryNetworkMonitorResults


## 描述
查询网络类型任务拨测结果

## 请求方式
GET

## 请求地址
https://detection.jdcloud-api.com/v3/netMonitorResult


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**taskId**|Long|True| |任务Id|
|**startTime**|Long|True| |开始时间 时间戳 需小于当前时间|
|**endTime**|Long|True| |结束时间 时间戳 需大于开始时间|
|**pageIndex**|Integer|True| |当前页码 需大于等于1|
|**pageSize**|Integer|True| |每页大小 取值范围1到500|
|**status**|Integer|False| |结果状态 0成功 1失败|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String|请求的标识id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean| |
|**message**|String| |
|**total**|Integer| |
|**data**|[Net[]](#net)| |
### <div id="Net">Net</div>
|名称|类型|描述|
|---|---|---|
|**url**|String|任务地址|
|**monitorIP**|String|拨测点IP|
|**monitorISP**|String|拨测点运营商|
|**monitorCountry**|String|拨测点国家|
|**monitorProvince**|String|拨测点省份|
|**monitorCity**|String|拨测点城市|
|**monitorDns**|String|拨测点DNS|
|**error**|String|错误信息|
|**errorCode**|Integer|错误码|
|**status**|Integer|状态 0:成功 1:失败|
|**dnsRecordType**|String|DNS记录类型|
|**dnsAddress**|String|DNS记录地址|
|**dnsQueryTime**|Integer|DNS解析用时|
|**dnsDetail**|String|DNS详情|
|**pingCname**|String|CANME|
|**pingHost**|String|PING HOST|
|**pingIp**|String|PING IP|
|**pingPort**|Long|PING TCP PORT|
|**pingPackets**|Integer|PING 总包数|
|**pingPacketsLoss**|Double|PING 丢包率|
|**pingSuccessPackets**|Integer|PING 成功包数|
|**pingFailPackets**|Integer|PING 失败包数|
|**pingSize**|Integer|PING 包大小|
|**pingAvgTs**|Integer|PING 平均耗时|
|**pingMaxTs**|Integer|PING 最大耗时|
|**pingMinTs**|Integer|PING 最小耗时|
|**pingMDevTs**|Integer|PING Mean Deviation， ICMP包的 RTT 偏离平均值的程度|
|**pingTsList**|String|PING 耗时列表, -1为请求超时  "[49,49,52,46]"|
|**pingTtlList**|String|PING ttlList列表 "[48,48,48,48]"|
|**pingTtl**|Integer|PING 平均ttl|
|**tracerMaxHop**|Integer|tracer 最大跳数|
|**tracerAvgTs**|Long|tracer 平均时延|
|**tracerCname**|String|tracer cname|
|**tracerIp**|String|tracer ip|
|**tracerHops**|String|tracer 每一跳的信息 [{"ip":"10.207.0.1","cn":"","ts":3}]|
|**tracerHopNum**|Integer|tracer 跳跃数量|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||拨测结果列表|
