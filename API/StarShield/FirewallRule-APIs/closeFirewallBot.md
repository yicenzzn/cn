# closeFirewallBot


## 描述
关闭BOT

## 请求方式
DELETE

## 请求地址
https://starshield.jdcloud-api.com/v1/bot/{zoneId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zoneId**|String|True| | |

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](closeFirewallBot#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean|操作是否成功|

## 返回码
|返回码|描述|
|---|---|
|**200**|request successful|
