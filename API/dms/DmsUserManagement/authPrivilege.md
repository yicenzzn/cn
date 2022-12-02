# authPrivilege


## 描述
实例授权

## 请求方式
POST

## 请求地址
https://dms.jdcloud-api.com/v1/management:authPrivilege


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pinList**|String[]|True| |用户pin列表信息|
|**privilegeName**|String|True| |权限名称,枚举值：PrivilegeLogin(实例登录权限)|
|**expireDate**|String|True| |授权过期时间(yyyy-MM-dd'T'HH:mm:ss.SSS'Z')|
|**dmsPrivilegeInstanceParamList**|[DmsPrivilegeInstanceParam[]](#dmsprivilegeinstanceparam)|True| |授权实例的信息，主要包括用户实例ID和实例名称|

### <div id="DmsPrivilegeInstanceParam">DmsPrivilegeInstanceParam</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例Id。|
|**instanceName**|String|True| |实例名称。|
|**instanceType**|String|True| |实例类型。|
|**regionId**|String|True| |实例所属区域。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
