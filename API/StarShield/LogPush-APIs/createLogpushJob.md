# createLogpushJob


## 描述
为域创建新的日志推送作业

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/logpush$$jobs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_name**|String|False| |域名|
|**destination_conf**|String|False| |唯一标识数据推送目的地的字符串。可能包括目的地支持的其他参数。<br>例如：splunk://splunk.cf-analytics.com:8088/services/collector/raw?channel=xxx&header_Authorization=Splunk xxx&sourcetype=xxx&insecure-skip-verify=false<br>|
|**name**|String|False| |可选的用户可读的作业名称。不是独一无二的。使用户更容易识别工作。建议包含域名称。|
|**enabled**|Boolean|False| |默认值false|
|**dataset**|String|False| |要推送的数据集。合法值为：http/firewall。|
|**logpull_options**|String|False| |它指定了诸如请求的字段和时间戳格式之类的内容。例如：fields=fieldName1,fieldName2,fileNamek&timestamps=rfc3339&sample=0.1|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createLogpushJob#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[LogpushJob](createLogpushJob#logpushjob)| |
### <div id="logpushjob">LogpushJob</div>
|名称|类型|描述|
|---|---|---|
|**zone_name**|String|域名|
|**enabled**|Boolean| |
|**last_complete**|String|记录上次成功推送日志的时间。如果上次成功推送的日志范围为2018-07-23T10:00:00Z至2018-07-23T10:01:00Z，则该字段的值将为2018-07-23T10:01:00Z。如果作业从未运行或刚刚启用但尚未运行，则该字段将为空。|
|**logpull_options**|String|它指定了诸如请求的字段和时间戳格式之类的内容。|
|**name**|String|可选的用户可读的作业名称。不是独一无二的。使用户更容易识别工作。建议包含域名称。|
|**error_message**|String|如果不为null，则表示作业当前失败。失败通常是重复的（例如：没有写入目标存储桶的权限）。只记录最后一次故障。成功执行作业时，错误消息和最后一个错误被设置为null。|
|**destination_conf**|String|唯一标识数据推送目的地的字符串。可能包括目的地支持的其他参数。|
|**path**|String|唯一标识数据推送目的地的字符串。|
|**service**|String|服务名称，例如Amazon S3, Splunk。|
|**dataset**|String|要推送的数据集。|
|**id**|Integer|作业的唯一id。|
|**frequency**|String|星盾向目标发送成批日志的频率。将“频率”设置为“高”会将日志发送到更多更小的文件中。将“频率”设置为“低”会以较小数量的较大文件发送日志。|
|**last_error**|String|记录上次作业失败的时间。如果不为null，则表示作业当前失败。如果为null，则表示作业从未失败，或者自上次失败以来至少成功运行过一次。另请参见错误消息字段。|
|**status**|String|推送状态，合法值：Pushing-正在推送，Error-推送失败，Off-关闭|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
