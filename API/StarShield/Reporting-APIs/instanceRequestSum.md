# instanceRequestSum


## 描述
总请求量。查询范围最近6个月、查询最大跨度1个月。

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/instances/{instanceId}/instanceRequestSum

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例标识|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**queryMode**|String|True| |all - 所有<br>normal - 业务<br>mitigation - 缓解<br>cache - 缓存<br>origin - 回源<br>|
|**since**|String|True| |查询开始时间|
|**until**|String|True| |查询结束时间|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](instanceRequestSum#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**value**|Number|单指标的值<br>如果是带宽，值的单位是bps（bit per second）<br>如果是流量，值的单位是Byte<br>如果是请求量，值的单位是次数<br>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
