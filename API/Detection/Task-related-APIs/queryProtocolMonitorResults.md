# queryProtocolMonitorResults


## 描述
查询协议类型任务拨测结果

## 请求方式
GET

## 请求地址
https://detection.jdcloud-api.com/v3/protocolMonitorResult


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
|**data**|[Protocol[]](#protocol)| |
### <div id="Protocol">Protocol</div>
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
|**ip**|String|目标地址IP|
|**port**|Integer|端口|
|**validResult**|Integer|验证结果 0 未验证 1验证成功 2验证失败|
|**dnsTime**|Long|dns解析耗时|
|**tcpTime**|Long|tcp连接耗时|
|**requestTime**|Long|请求耗时|
|**responseTime**|Long|响应耗时|
|**sslTime**|Long|ssl耗时|
|**waitTime**|Long|整体耗时|
|**responseData**|String|响应内容|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||拨测结果列表|
