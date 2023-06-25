
# assumeRole

## 描述
扮演用户角色，获取临时凭证

## 请求方式
POST

## 请求地址
https://sts.jdcloud-api.com/v1/sessionToken:assumeRole

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**assumeRoleInfo**|AssumeRoleInfo|True| | |

### AssumeRoleInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleJrn**|String|True| |角色资源标识(jrn)|
|**roleSessionName**|String|True| |角色会话名称|
|**policy**|String|False|  |会话策略，策略描述需遵循 IAM 策略语法，但不可包含 Principal元素，长度限制 2048 字节。会话策略限制临时凭证的权限；如不指定，则临时凭证默认拥有附加到角色的所有权限。|
|**durationSeconds**|Integer|False|  |临时凭证有效期，单位秒，取值范围：3600~您所扮演的角色设置的maxSessionDuration，默认3600|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**result**|Credentials| |

### Credentials
|名称|类型|描述|
|---|---|---|
|**accessKey**|String|临时accessKey|
|**secretKey**|String|临时secretKey|
|**sessionToken**|String|临时安全令牌|
|**expiration**|String|失效时间，格式：yyyy-MM-dd HH:mm:ss(eg 2019-01-01 00:00:00)|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
