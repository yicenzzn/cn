# requestTopK


## 描述
按域名的TopK总请求量。查询范围最近6个月、查询最大跨度1个月。

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/instances/{instanceId}/requestTopK

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
|**result**|[Result](requestTopK#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[TopK](requestTopK#topk)| |
### <div id="topk">TopK</div>
|名称|类型|描述|
|---|---|---|
|**topK**|[Item[]](requestTopK#item)|排名前K的项。|
### <div id="item">Item</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|项的名称|
|**value**|Number|项的值。<br>如果是带宽，值的单位是bps（bit per second）<br>如果是流量，值的单位是Byte<br>如果是请求量，值的单位是次数<br>|
|**unit**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
