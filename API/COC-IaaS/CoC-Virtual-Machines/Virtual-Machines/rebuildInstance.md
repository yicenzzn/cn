# rebuildInstance


## 描述
重置合作云主机系统。

## 接口说明
- 合作云主机的状态必须为 `stopped` 状态。
- 若实例基于私有镜像创建，而私有镜像已被删除，则无法使用原镜像重置系统，即无法恢复至刚创建时的系统状态，建议保留被实例引用的私有镜像。
- 重置系统需要重新指定密码，对于 `Linux` 系统您还可以重新指定 `SSH密钥`。
- 对于云盘作系统盘的实例，当前系统盘大小不能超过目标镜像对应系统盘快照的容量。
- 暂不支持Linux与Windows操作系统间相互重置。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:rebuildInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**password**|String|False| |实例密码。<br>可用于SSH登录和VNC登录。<br>长度为8-26个字符，必须同时包含大、小写英文字母、数字和特殊符号中的三类字符。特殊符号包括：\(\)\~!@#$%^&\*\_-+=\|{}\[ ]:";'<>,.?/，`。<br>密码和密钥只支持一个。<br>|
|**imageId**|String|False| |镜像ID。<br>若不指定镜像ID，默认使用当前主机的原镜像重置系统。<br>|
|**keyNames**|String[]|False| |密钥对名称。<br>仅Linux系统下该参数生效，当前仅支持输入单个密钥。<br>密码和密钥只支持一个。<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求ID。|


## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|
