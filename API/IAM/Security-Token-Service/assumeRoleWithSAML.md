
# assumeRoleWithSAML

## 描述
进行角色SSO时，通过调用AssumeRoleWithSAML接口，可以获取一个扮演该角色的临时身份。

## 请求方式
POST

## 请求地址
https://sts.jdcloud-api.com/v1/sessionToken:assumeRoleWithSAML

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**assumeRoleWithSAMLInfo**|AssumeRoleWithSAMLInfo|True| |角色代入参数|

### AssumeRoleWithSAMLInfo
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**roleJrn**|String|True| |角色资源标识(jrn)|
|**samlProviderJrn**|String|True| |身份提供商资源标识(jrn)|
|**policy**|String|False|  |会话策略，压缩后不超过1024字节|
|**durationSeconds**|Integer|False|  |临时凭证有效期，单位秒，取值范围：3600~您所扮演的角色设置的maxSessionDuration，默认3600|
|**samlAssertion**|String|True| |SAML断言（Base64编码）|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**credentials**|Credentials|凭证信息|
|**samlAssertionInfo**|SamlAssertionInfo|SAML断言中的部分信息|

### Credentials
|名称|类型|描述|
|---|---|---|
|**accessKey**|String|临时accessKey|
|**secretKey**|String|临时secretKey|
|**sessionToken**|String|临时安全令牌|
|**expiration**|String|失效时间，格式：yyyy-MM-dd HH:mm:ss(eg 2019-01-01 00:00:00)|

### SamlAssertionInfo
|名称|类型|描述|
|---|---|---|
|**subjectType**|String|SAML断言中NameID的格式|
|**subject**|String|SAML断言中Subject.NameID字段值|
|**recipient**|String|SAML断言中Subject.SubjectConfirmation.SubjectConfirmationData字段中Recipient字段值|
|**issuer**|String|SAML断言中Issuer字段值|


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
