# checkDestinationExists


## 描述
检查是否存在作业，处理该目标。

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/logpush$$validate$$destination$$exists

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**destination_conf**|String|False| |唯一标识数据推送目的地的字符串。可能包括目的地支持的其他参数。<br>例如：splunk://splunk.cf-analytics.com:8088/services/collector/raw?channel=xxx&header_Authorization=Splunk xxx&sourcetype=xxx&insecure-skip-verify=false<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](checkDestinationExists#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|Boolean| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
