# queryTypeInstance


## 描述
查询用户数据类型实例

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/regions/{regionId}/typeInstances:query

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dbType**|Integer|False| |数据源类型，CDS("CDS", 1), MYSQL("MYSQL", 2), ORACLE("ORACLE", 3), SQLSERVER("SQLSERVER", 4), CDSMYSQL("CDSMYSQL", 5), CDSORACLE("CDSORACLE", 6), CDSSQLSERVER("CDSSQLSERVER", 7), DATACENTER("DATACENTER", 8), HBASE("Hbase",9),MONGODB("MongoDb",10),ES("ES",11), MYSQL_INS("MYSQL_INS",12), DRDS_INS("DRDS_INS",13), STARDB_INS("STARDB_INS",14), STARDB_PROXY_INS("STARDB_PROXY_INS",15), CLICK_HOUSE_INS("CLICK_HOUSE_INS",16), TIDB_INS("TIDB_INS",17), OPEN_GAUSS_INS("OPEN_GAUSS_INS",18), SS_OPEN_GAUSS_INS("SS_OPEN_GAUSS_INS",19);|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|[String](#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**regionId**|String|查询分类方式：LOGIN_STATUS，DB_TYPE。|
|**dbType**|Integer|数据库类型。|
|**loginedInstance**|[DmsInstance[]](#dmsinstance)|已登录实例。|
|**unloginedInstance**|[DmsInstance[]](#dmsinstance)|未登录实例。|
### <div id="dmsinstance">DmsInstance</div>
|名称|类型|描述|
|---|---|---|
|**dbType**|Integer|数据库类型，CDS("CDS", 1), MYSQL("MYSQL", 2), ORACLE("ORACLE", 3), SQLSERVER("SQLSERVER", 4), CDSMYSQL("CDSMYSQL", 5), CDSORACLE("CDSORACLE", 6), CDSSQLSERVER("CDSSQLSERVER", 7), DATACENTER("DATACENTER", 8), HBASE("Hbase",9),MONGODB("MongoDb",10),ES("ES",11), MYSQL_INS("MYSQL_INS",12), DRDS_INS("DRDS_INS",13), STARDB_INS("STARDB_INS",14), STARDB_PROXY_INS("STARDB_PROXY_INS",15), CLICK_HOUSE_INS("CLICK_HOUSE_INS",16), TIDB_INS("TIDB_INS",17), OPEN_GAUSS_INS("OPEN_GAUSS_INS",18), SS_OPEN_GAUSS_INS("SS_OPEN_GAUSS_INS",19);。|
|**dataSource**|[DataSource](#datasource)|数据源详情。|
|**instanceInfo**|Object|从RDS，DRDS获取的数据源详情。|
### <div id="datasource">DataSource</div>
|名称|类型|描述|
|---|---|---|
|**id**|Integer|主键id。|
|**ip**|String|数据库ip地址。|
|**port**|Integer|数据库端口。|
|**dbName**|String|dbName，数据库名称，RDS或DRDS实例时为空。|
|**modifiedBy**|String|修改用户。|
|**status**|String|0为有效，1为无效。|
|**userName**|String|数据库用户名。|
|**passwd**|String|数据库密码。|
|**passwdEcrypt**|String|数据库加密密码。|
|**cdsCluster**|String|Cds集群名称。|
|**dbType**|Integer|数据库类型，CDS("CDS", 1), MYSQL("MYSQL", 2), ORACLE("ORACLE", 3), SQLSERVER("SQLSERVER", 4), CDSMYSQL("CDSMYSQL", 5), CDSORACLE("CDSORACLE", 6), CDSSQLSERVER("CDSSQLSERVER", 7), DATACENTER("DATACENTER", 8), HBASE("Hbase",9),MONGODB("MongoDb",10),ES("ES",11), MYSQL_INS("MYSQL_INS",12), DRDS_INS("DRDS_INS",13),STARDB_INS("STARDB_INS",14), STARDB_PROXY_INS("STARDB_PROXY_INS",15), CLICK_HOUSE_INS("CLICK_HOUSE_INS",16), TIDB_INS("TIDB_INS",17), OPEN_GAUSS_INS("OPEN_GAUSS_INS",18), SS_OPEN_GAUSS_INS("SS_OPEN_GAUSS_INS",19);|
|**createTime**|String|创建时间。|
|**environmentType**|Integer|环境类型，已废弃。|
|**dbTypeName**|String|已废弃。|
|**sensitivity**|String|已废弃。|
|**userType**|Integer|已废弃。|
|**mongoAuth**|String|mongo权限类型。|
|**schemaCname**|String|数据库中文名备注，已废弃。|
|**schemaDepartment**|String|数据库所属部门，已废弃。|
|**schemaDba**|String|数据库维护dba，已废弃。|
|**schemaOwner**|String|数据库owner，已废弃。|
|**isStandard**|String|已废弃。|
|**coldict**|String|已废弃。|
|**version**|String|数据库版本，已废弃。|
|**schemaEnvironment**|String|数据库环境，已废弃。|
|**query**|String|已废弃。|
|**region**|String|数据库所属区域。|
|**addrMode**|String|地址模式：CLASSIC("CLASSIC", 0), RDS("RDS", 1), ECS("ECS", 2), VPC("VPC", 3);。|
|**addrOrigin**|String|原生地址，RDS，DRDS为实例id。|
|**addrKey**|String|保留字段。|
|**extra**|String|保留字段。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
