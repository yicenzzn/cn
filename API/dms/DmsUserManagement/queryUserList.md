# queryUserList


## 描述
用户管理列表

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:queryUserList


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**activeStatus**|Boolean|False| |查询的用户状态(启用(true),禁用(false))|
|**role**|String|False| |查询的用户角色,枚举值(Admin("Admin","管理员"),DBA("DBA","DBA"),StructureReadOnly("StructureReadOnly","结构只读"),Normal("Normal","普通用户"))|
|**loginDateStart**|String|False| |查询的用户登录开始时间(yyyy-MM-dd'T'HH:mm:ss.SSS'Z')|
|**loginDateEnd**|String|False| |查询的用户登录结束时间(yyyy-MM-dd'T'HH:mm:ss.SSS'Z')|
|**username**|String|False| |查询用户的用户名称|
|**pageNumber**|Integer|False| |显示数据的页码，取值范围：[1,∞)。pageNumber为Null时，返回所有数据页码；超过总页数时，无数据。|
|**pageSize**|Integer|False| |每页显示的数据条数，用于查询列表的接口。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|[String](#result)|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**count**|Integer|符合条件的用户的总数|
|**dmsUserVOList**|[DmsUserVO[]](#dmsuservo)| |
### <div id="DmsUserVO">DmsUserVO</div>
|名称|类型|描述|
|---|---|---|
|**username**|String|用户名。|
|**pin**|String|用户pin。|
|**masterPin**|String|用户对应的的主账号的pin。|
|**isMaster**|Boolean|用户是否是主账号。|
|**accountId**|Long|用户账号Id。|
|**phone**|String|用户手机号码。|
|**email**|String|用户邮箱。|
|**activeStatus**|String|用户的启用状态。|
|**deleteStatus**|String|用户的删除状态。|
|**addDate**|String|用户的添加时间，格式为：yyyy-MM-dd'T'HH:mm:ss|
|**loginDate**|String|用户的登录时间，格式为：yyyy-MM-dd'T'HH:mm:ss|
|**createDate**|String|用户的创建时间，格式为：yyyy-MM-dd'T'HH:mm:ss|
|**modifiedDate**|String|用户的修改时间，格式为：yyyy-MM-dd'T'HH:mm:ss|
|**roleVOList**|[DmsRoleVO[]](#dmsrolevo)|用户角色列表。|
### <div id="DmsRoleVO">DmsRoleVO</div>
|名称|类型|描述|
|---|---|---|
|**roleName**|String|角色名称。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
