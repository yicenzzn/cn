# tableInfo


## 描述
获取表元数据，支持Mysql，Stardb，Tidb，ClickHouse

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/consoleTableInfo

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataSourceId**|Integer|True| |数据源id|
|**dbName**|String|True| |库名。|
|**tableName**|String|True| |表名。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](tableinfo#result)| |
|**requestId**|[String](tableinfo#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dmsTableStruct**|[DmsTableStruct](tableinfo#dmstablestruct)| |
### <div id="dmstablestruct">DmsTableStruct</div>
|名称|类型|描述|
|---|---|---|
|**tableName**|String|表名。|
|**primaryIndex**|String|主键。|
|**sql**|String|建表sql|
|**metaTableInfo**|[MetaTableInfo](tableinfo#metatableinfo)| |
|**columnInfos**|[ColumnInfo[]](tableinfo#columninfo)|表中全部列信息。|
|**indexInfos**|[IndexInfo[]](tableinfo#indexinfo)|表中全部索引信息。|
|**extraTableInfo**|[ExtraTableInfo](tableinfo#extratableinfo)|广播表，分表额外信息。|
### <div id="extratableinfo">ExtraTableInfo</div>
|名称|类型|描述|
|---|---|---|
|**tableTypeEnum**|String|ORIGIN:原始表, STARDB_SPLIT:stardb切分表, STARDB_ISOLATE:stardb孤立表, STARDB_BROADCAST:stardb广播表。|
|**stardbSplitInfo**|[StardbSplitInfo](tableinfo#stardbsplitinfo)|tableTypeEnum为切分表时的切分信息内容。|
### <div id="stardbsplitinfo">StardbSplitInfo</div>
|名称|类型|描述|
|---|---|---|
|**splitType**|String|切分方式，"MODULO：取模, "HASH"：哈希, "DB_TABLE"：分库分表, "YYYYMMDD","YYYYMM","MM","MMDD"|
|**tableSplitCount**|Integer|切分表数量,表切分方式为哈希取模时必需|
|**columnNames**|String[]|切分列名称，第一项为切分表的列（必需），第二项为切分库的列（非必需)|
|**splitDateBegin**|String|起始时间，切分方式为时间时必需，格式为20220125|
|**splitDateEnd**|String|结束时间，切分方式为时间时必需，格式为20220125|
### <div id="indexinfo">IndexInfo</div>
|名称|类型|描述|
|---|---|---|
|**indexName**|String|索引名。|
|**indexType**|String|列类型，普通索引：NORMAL，唯一索引：UNIQUE。|
|**columnNames**|String[]|列名称。|
### <div id="columninfo">ColumnInfo</div>
|名称|类型|描述|
|---|---|---|
|**columnName**|String|列名。|
|**newColumnName**|String|新列名，修改表结构时使用。|
|**dataType**|String|列类型。|
|**columnType**|String|列类型, 返回int(3), varchar(64)等。|
|**columnLength**|Integer|列长度。|
|**columnScale**|Integer|浮点数小数点后位数。|
|**isNull**|Boolean|是否为空。|
|**defaultValue**|String|默认值。|
|**columnComment**|String|列注释。|
|**isAutoIncrease**|Boolean|是否自增。|
|**isPrimaryKey**|Boolean|是否为主键。|
### <div id="metatableinfo">MetaTableInfo</div>
|名称|类型|描述|
|---|---|---|
|**tableName**|String|表名。|
|**tableComment**|String|表注释。|
|**tableCharset**|String|表字符编码。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
