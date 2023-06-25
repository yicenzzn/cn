# getEvidence


## 描述
单证据链取证接口

## 请求方式
GET

## 请求地址
https://cloudsign.jdcloud-api.com/v1/evidence:evidenceGetEvidence


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**businessId**|String|True| |业务流水号|
|**evidenceId**|String|True| |存证编号|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getevidence#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**code**|String| |
|**message**|String| |
|**success**|Boolean| |
|**data**|[GetEvidenceResp](getevidence#getevidenceresp)| |
### <div id="getevidenceresp">GetEvidenceResp</div>
|名称|类型|描述|
|---|---|---|
|**evidenceId**|String|存证编号|
|**messageId**|String|取证请求流水号（单证据链存证用户无需关心）|
|**evidenceMessageId**|String|存证请求的流水号（单证据链存证用户无需关心）|
|**evidenceFileList**|Object[]|取证结果文件|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|