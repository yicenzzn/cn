# fieldsDefault


## 描述
数据集可用的所有默认字段列表。

## 请求方式
GET

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/logpush$$datasets/{dataset}/fieldsDefault

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |
|**dataset**|String|True| | |

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](fieldsDefault#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dataList**|[LogModule[]](fieldsDefault#logmodule)| |
### <div id="logmodule">LogModule</div>
|名称|类型|描述|
|---|---|---|
|**moduleName**|String|日志模块名称|
|**moduleFields**|[LogField[]](fieldsDefault#logfield)|日志模块字段成员|
### <div id="logfield">LogField</div>
|名称|类型|描述|
|---|---|---|
|**fieldName**|String|日志字段名称|
|**fieldType**|String|日志字段类型|
|**fieldDescription**|String|日志字段描述|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
