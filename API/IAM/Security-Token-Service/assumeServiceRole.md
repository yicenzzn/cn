
# assumeServiceRole

## 描述
服务角色与服务相关角色代入

## 请求方式
POST

## 请求地址
https://sts.jdcloud-api.com/v1/assumedServiceRole/{assumedServiceRoleName}/credentials

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**assumedServiceRoleName**|String|True| | service role name|

## 请求参数
### AssumeServiceRoleInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleType**|Integer|True| |角色类型, 1-服务相关角色，2-服务角色|
|**durationSeconds**|Integer|False|  |令牌有效期，单位秒，默认3600|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**credentials**|Credentials|凭证信息|
|**assumedRoleUser**|AssumedRoleService|代入角色服务信息|

### Credentials
|名称|类型|描述|
|---|---|---|
|**accessKey**|String|临时accessKey|
|**secretKey**|String|临时secretKey|
|**sessionToken**|String|临时安全令牌|
|**expiration**|String|失效时间，格式：yyyy-MM-dd HH:mm:ss(eg 2019-01-01 00:00:00)|

### AssumedRoleService
|名称|类型|描述|
|---|---|---|
|**assumedServiceRoleId**|String|代入角色id|
|**assumedServiceRoleName**|String|代入角色名|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
