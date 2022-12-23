# queryProtocolAvgMetrics


## 描述
查询协议类型任务平均指标数据

## 请求方式
GET

## 请求地址
https://detection.jdcloud-api.com/v3/protocolAvgMetrics


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**taskId**|Long|True| |任务Id|
|**startTime**|Long|True| |开始时间 时间戳 需小于当前时间|
|**endTime**|Long|True| |结束时间 时间戳 需大于开始时间|
|**duration**|Integer|False| |数据点间隔时间(分钟)，可选5/10/15/30/60/120/180/240/300/480/720，默认为任务调度周期，需大于任务调度周期|


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
|**data**|[ProtocolMetric[]](#protocolmetric)| |
### <div id="ProtocolMetric">ProtocolMetric</div>
|名称|类型|描述|
|---|---|---|
|**overallTime**|Long|整体性能(毫秒)|
|**dnsTime**|Long|DNS用时(毫秒)|
|**sslTime**|Long|SSL握手用时(毫秒)|
|**tcpTime**|Long|TCP用时(毫秒)|
|**requestTime**|Long|请求用时(毫秒)|
|**responseTime**|Long|响应用时(毫秒)|
|**timestamp**|Long|时间戳|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||拨测协议类型任务平均指标数据|
