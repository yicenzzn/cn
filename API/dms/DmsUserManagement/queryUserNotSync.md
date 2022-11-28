# queryUserNotSync


## 描述
获取主账号下未同步的子账号数据

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:queryUserNotSync


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |第几页,不传的话会将当前所有的未同步的账号都同步过来|
|**pageSize**|Integer|False| |页大小。|
|**keyword**|String|False| |关键字。|
|**sort**|Integer|False| |排序规则：0-创建时间顺序排序，1-创建时间倒序排序。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|[String](#result)|请求id|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Integer|子账号总数量|
|**subUserList**|[DmsSubUserVO[]](#dmssubuservo)|子用户列表信息|
### <div id="DmsSubUserVO">DmsSubUserVO</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|子用户名。|
|**phone**|String|手机号码。|
|**email**|String|邮箱。|
|**description**|String|描述信息。|
|**account**|String|主账号。|
|**pin**|String|子账号pin。|
|**createTime**|String|用户创建时间。|
|**updateTime**|String|用户更新时间。|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
