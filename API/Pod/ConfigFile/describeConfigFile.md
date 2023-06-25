# describeConfigFile


## 描述
查询单个 ConfigFile 详情。


## 请求方式
GET

## 请求地址
https://pod.jdcloud-api.com/v1/regions/{regionId}/configFiles/{name}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域 ID。|
|**name**|String|True| |ConfigFile名称。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeConfigFile#result)| 响应结果。|
|**requestId**|String|请求ID。 |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**configFile**|[ConfigFile](describeConfigFile#configfile)|ConfigFile详情。 |

### <div id="configFile">ConfigFile</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|ConfigFile名称。|
|**data**|[ConfigFileData[]](describeconfigfile#configfiledata)|ConfigFile数据。|

### <div id="configfiledata">ConfigFileData</div>
|名称|类型|描述|
|---|---|---|
|**key**|String|键。|
|**value**|String|值，返回结果为base64后的内容。|

## 返回码
|HTTP状态码|错误码|描述|错误解析
|---|---|---|---|
|**200**||OK|
|**404**|NOT_FOUND | ConfigFile xx not found| ConfigFile xx 未找到。
|**500**| INTERNAL| Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。
|**500**|	UNKNOWN|	Unknown server error	|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。
