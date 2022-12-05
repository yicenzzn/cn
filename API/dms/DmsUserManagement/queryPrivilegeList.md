# queryPrivilegeList


## 描述
用户授权信息列表

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:queryPrivilegeList


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|False| |实例ID|
|**instanceName**|String|False| |实例名称|
|**pin**|String|False| |用户账号|
|**showNormal**|Boolean|False| |是否只显示生效中的授权信息|
|**releaseStatus**|Boolean|False| |是否只显示释放的记录,true展示释放权限的记录|
|**pageNumber**|Integer|False| |显示数据的页码，取值范围：[1,∞)。pageNumber为Null时，返回所有数据页码；超过总页数时，无数据。|
|**pageSize**|Integer|False| |每页显示的数据条数，用于查询列表的接口。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](queryprivilegelist#result)| |
|**requestId**|[String](queryprivilegelist#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**count**|Integer|符合条件的用户的总数|
|**isAdmin**|Boolean|如果为真则表示这个账号默认就拥有所有的实例登录权限|
|**dmsPrivilegeVOList**|[DmsPrivilegeVO[]](queryprivilegelist#dmsprivilegevo)| |
### <div id="dmsprivilegevo">DmsPrivilegeVO</div>
|名称|类型|描述|
|---|---|---|
|**id**|Long|主键Id。|
|**username**|String|用户名。|
|**pin**|String|用户pin。|
|**privilegeName**|String|用户权限名称。|
|**instanceId**|String|实例ID。|
|**instanceName**|String|实例名称。|
|**databaseName**|String|数据库库名。|
|**tableName**|String|表名。|
|**fieldName**|String|字段名称。|
|**authStatus**|String|授权状态。|
|**authDate**|String|授权时间|
|**expireDate**|String|过期时间|
|**releaseStatus**|Boolean|权限是否已经释放。|
|**instanceType**|String|实例类型。|
|**regionId**|String|实例所属区域。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
