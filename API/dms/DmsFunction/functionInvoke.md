# functionInvoke


## 描述
调用函数，支持Mysql

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/function:invoke

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |数据库名称。|
|**functionName**|String|True| |函数名称。|
|**parameters**|[Parameter[]](functioninvoke#parameter)|False| |参数。|

### <div id="parameter">Parameter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |参数名称。|
|**columnTypeEnum**|String|True| |列类型，TINYINT("TINYINT", 0), SMALLINT("SMALLINT", 1), MEDIUMINT("MEDIUMINT", 2), INT("INT", 3), BIGINT("BIGINT", 4), INTEGER("INTEGER", 5), FLOAT("FLOAT", 6), DOUBLE("DOUBLE", 7), REAL("REAL", 8), DECIMAL("DECIMAL", 9), CHAR("CHAR", 10), VARCHAR("VARCHAR", 11), TINYTEXT("TINYTEXT", 12), TEXT("TEXT", 13), MEDIUMTEXT("MEDIUMTEXT", 14), LONGTEXT("LONGTEXT", 15), DATE("DATE", 16), DATETIME("DATETIME", 17), TIMESTAMP("TIMESTAMP", 18), TIME("TIME", 19), YEAR("YEAR", 19), BINARY("BINARY", 20), VARBINARY("VARBINARY", 21), TINYBLOB("TINYBLOB", 22), BLOB("BLOB", 23), MEDIUMBLOB("MEDIUMBLOB", 24), LONGBLOB("LONGBLOB", 25);|
|**parameterModeEnum**|String|True| |参数模式，IN("IN", 0), OUT("OUT", 1), INOUT("INOUT", 2);|
|**value**|String|True| |函数调用时传入值;|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](functioninvoke#result)| |
|**requestId**|[String](functioninvoke#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**returnValue**|String|返回值|
|**outArgs**|Object[]|输出参数返回值列表|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
