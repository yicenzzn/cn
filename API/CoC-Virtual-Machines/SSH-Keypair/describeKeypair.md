# describeKeypair


## 描述
查询密钥详情。


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/keypairs/{keyName}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**keyName**|String|True| |密钥名称。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeKeypair#result)|密钥详情信息。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**keypairDetail**|[KeypairDetail](describeKeypair#Keypairdetail)| |
### <div id="KeypairDetail">KeypairDetail</div>
|名称|类型|描述|
|---|---|---|
|**keyName**|String|密钥对名称。|
|**publicKey**|String|公钥。|
|**keyFingerprint**|String|密钥对的指纹，根据 `RFC4716` 定义的公钥指纹格式，采用 `MD5` 信息摘要算法。|
|**createTime**|String|密钥对创建时间。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|
