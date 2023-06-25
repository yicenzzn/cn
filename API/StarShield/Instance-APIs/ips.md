# ips


## 描述
星盾节点信息

## 请求方式
GET

## 请求地址
https://starshield.jdcloud-api.com/v1/regions/{regionId}/ips

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](ips#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**jdcloudCidrs**|String[]|星盾节点信息jdcloud_cidrs|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
