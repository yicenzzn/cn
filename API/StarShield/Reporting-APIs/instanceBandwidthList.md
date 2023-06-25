# instanceBandwidthList


## 描述
域名带宽列表，按带宽降序排列。查询范围最近6个月、查询最大跨度1个月。

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/instances/{instanceId}/instanceBandwidthList

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例标识|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**queryMode**|String|True| |all - 所有<br>normal - 业务<br>mitigation - 缓解<br>cache - 缓存<br>origin - 回源<br>|
|**since**|String|True| |查询开始时间|
|**until**|String|True| |查询结束时间|
|**pageNumber**|Integer|True| |页码。当页码为-1时，返回所有记录|
|**pageSize**|Integer|False| |每页显示记录数。当pageNumber的值大于0时，该字段必须赋值|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](instanceBandwidthList#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Number| |
|**cdnZoneBandwidths**|[CdnZoneBandwidth[]](instanceBandwidthList#cdnzonebandwidth)| |
### <div id="cdnzonebandwidth">CdnZoneBandwidth</div>
|名称|类型|描述|
|---|---|---|
|**zoneName**|String|域名|
|**maxBPS**|Double|带宽峰值，单位bps（bit per second）|
|**maxBpsTs**|Number|带宽峰值的发生时间。值为时间戳对应的long值。|
|**trafficSum**|Double|总流量，单位Byte|
|**requestSum**|Double|总请求量，单位次数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
