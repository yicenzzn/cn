# generalAlterEvent


## 描述
生成修改事件sql语句，支持Mysql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/event:generalAlter

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id。|
|**dbName**|String|True| |数据库名称。|
|**originEventName**|String|True| |原始事件名称。|
|**eventName**|String|True| |新事件名称。|
|**eventComment**|String|False| |注释。|
|**eventStatus**|String|False| |状态，ENABLED,DISABLED, SLAVESIDE_DISABLED。|
|**isPreserve**|Boolean|True| |完成后是否保存。|
|**eventDefinition**|String|True| |事件定义。|
|**eventType**|String|True| |调度方式，ONE_TIME,RECURRING。|
|**executeAt**|String|False| |执行一次的时间。|
|**intervalValue**|String|False| |循环执行时间隔时间的值。|
|**intervalField**|String|False| |循环执行时间隔时间的单位，YEAR,QUARTER,MONTH,WEEK,DAY,HOUR,MINUTE,SECOND,YEAR_MONTH,DAY_HOUR,DAY_MINUTE,DAY_SECOND,HOUR_MINUTE,HOUR_SECOND,MINUTE_SECOND。|
|**starts**|String|False| |循环执行开始时间。|
|**ends**|String|False| |循环执行结束时间。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](generalalterevent#result)| |
|**requestId**|[String](generalalterevent#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dmsSqls**|[DmsSql[]](generalalterevent#dmssql)|生成sql。|
### <div id="dmssql">DmsSql</div>
|名称|类型|描述|
|---|---|---|
|**sql**|String|SQL语句。|
|**sqlTypeEnum**|String|SQL类型：CREATE_VIEW，DROP_VIEW， ALTER_VIEW，CREATE_PROCEDURE，DROP_PROCEDURE， ALTER_PROCEDURE，CREATE_FUNCTION，DROP_FUNCTION， ALTER_FUNCTION，CREATE_TRIGGER，ALTER_TRIGGER，DROP_TRIGGER，CREATE_EVENT，ALTER_EVENT，DROP_EVENT。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
