# syncSubUser


## 描述
同步子账号

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:syncSubUser


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dmsSyncSubUserVOList**|[DmsSyncSubUserVO[]](#DmsSyncSubUserVO)|True| |同步的子账号的列表信息|

### <div id="DmsSyncSubUserVO">DmsSyncSubUserVO</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**username**|String|False| |子用户名。|
|**pin**|String|False| |子用户pin。|
|**phone**|String|False| |手机号。|
|**email**|String|False| |邮箱。|
|**roleList**|String[]|False| |角色信息。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
