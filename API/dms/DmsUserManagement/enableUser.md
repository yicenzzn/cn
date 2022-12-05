# enableUser


## 描述
启用/禁用用户

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:enableUser


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dmsUserEnableVOList**|[DmsUserEnableVO[]](#DmsUserEnableVO)|True| |启用/禁用的用户列表信息|

### <div id="DmsUserEnableVO">DmsUserEnableVO</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pin**|String|False| |用户pin。|
|**activeStatus**|Boolean|False| |用户的启用/禁用状态。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
