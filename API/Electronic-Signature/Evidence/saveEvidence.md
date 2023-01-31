# saveEvidence


## 描述
单证据链存证接口

## 请求方式
POST

## 请求地址
https://cloudsign.jdcloud-api.com/v1/evidence:evidenceSave


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**businessId**|String|True| |业务流水号|
|**file**|String|True| |存证数据json字符串的Base64|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](saveevidence#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**code**|String| |
|**message**|String| |
|**success**|Boolean| |
|**data**|[SaveEvidenceResp](saveevidence#saveevidenceresp)| |
### <div id="saveevidenceresp">SaveEvidenceResp</div>
|名称|类型|描述|
|---|---|---|
|**evidenceId**|String|存证编号|
|**messageId**|String|请求流水号（单证据链存证用户无需关心）|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|