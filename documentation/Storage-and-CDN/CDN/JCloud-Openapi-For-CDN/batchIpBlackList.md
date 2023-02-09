# batchIpBlackList


## 描述
批量添加域名ip黑名单

## 请求方式
POST

## 请求地址
https://cdn.jdcloud-api.com/v1/batchIpBlackList


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**operateDomainRange**|String|False| |可选值。表示域名操作范围，只可指定为all或空（不传），all代表操作该账号下全量域名,全量域名个数应<=单次可批量操作的域名个数(默认30个)，为空时该参数不生效。|
|**domains**|String[]|False| |可选值。待操作的域名列表,个数默认限制30个。注意operateDomainRange和domains至少指定一个参数。operateDomainRange为all时该参数不生效。|
|**ipList**|String[]|True| |ip列表。最多50个|
|**forbidTime**|Long|False| |封禁时长，单位分钟。默认1440|
|**action**|String|True| |forbid or resume.代表封禁和解封。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|

