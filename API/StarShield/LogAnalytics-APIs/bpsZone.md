# bpsZone


## 描述
bps on Zone

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/bps

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**x-jdcloud-account-id**|String|True| |请求头：实例id|
|**zoneName**|String|False| | |
|**queryMode**|String|False| | |
|**since**|String|False| | |
|**until**|String|False| | |


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](bpsZone#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[SimpleDateHistogram](bpsZone#simpledatehistogram)| |
### <div id="simpledatehistogram">SimpleDateHistogram</div>
|名称|类型|描述|
|---|---|---|
|**dataSeries**|Number[]|数据点集合。<br>如果是带宽，数据点的单位是bps（bit per second）<br>如果是流量，数据点的单位是Byte<br>如果是请求量，数据点的单位是次数<br>|
|**timeSeries**|Number[]|时间点集合。时间点的值为时间戳对应的long值。|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
