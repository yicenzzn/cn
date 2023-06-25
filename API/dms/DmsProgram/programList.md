# programList


## 描述
获取视图列表，支持Mysql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/program:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称。|
|**filter**|String|False| |过滤条件。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](programlist#result)| |
|**requestId**|[String](programlist#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**viewNames**|String[]|视图名称列表|
|**procedureNames**|String[]|存储过程名称列表|
|**functionNames**|String[]|函数名称列表|
|**triggerNames**|String[]|触发器名称列表|
|**eventNames**|String[]|事件名称列表|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
