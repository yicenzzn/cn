# zoneRequestMultiDateHistogram


## 描述
多指标的请求量图。查询范围最近6个月、查询最大跨度1个月。

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/zoneRequestMultiDateHistogram

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| |域名标识|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**queryModes**|String[]|True| |all - 所有<br>normal - 业务<br>mitigation - 缓解<br>cache - 缓存<br>origin - 回源<br>all/normal/mitigation/cache/origin的任意组合<br>|
|**zoneName**|String|True| |域名|
|**since**|String|True| |开始时间|
|**until**|String|True| |结束时间|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](zoneRequestMultiDateHistogram#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dateHistograms**|[DateHistogram[]](zoneRequestMultiDateHistogram#datehistogram)| |
|**timeScope**|Number[]|时间点集合。时间点的值为时间戳对应的long值。|
|**since**|String| |
|**util**|String| |
### <div id="datehistogram">DateHistogram</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|项的名称|
|**timeseries**|Number[]|数据点集合。<br>如果是带宽，数据点的单位是bps（bit per second）<br>如果是流量，数据点的单位是Byte<br>如果是请求量，数据点的单位是次数<br>|
|**unit**|String| |
|**total**|Number|如果是带宽，它的单位是bps（bit per second），代表数据点中的最大值。<br>如果是流量，它的单位是Byte，代表数据点流量之和。<br>如果是请求量，它的单位是次数，代表数据点请求量之和。<br>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
