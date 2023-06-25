# describeKeypairs


## 描述
查询密钥对列表

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/keypairs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码；默认为1|
|**pageSize**|Integer|False|20|分页大小；默认为20；取值范围[20, 100]|
|**name**|String|False| |密钥对名称|
|**filters**|[Filter[]](#filter)|False| |keypairId  - 密钥对ID，精确匹配，支持多个<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**keypairs**|[Keypair[]](#keypair)| |
|**pageNumber**|Integer|页码；默认为1|
|**pageSize**|Integer|分页大小；默认为20；取值范围[20, 100]|
|**totalCount**|Integer|查询结果总数|
### <div id="Keypair">Keypair</div>
|名称|类型|描述|
|---|---|---|
|**keypairId**|String|密钥对id|
|**region**|String|地域|
|**name**|String|密钥对名称|
|**publicKey**|String|公钥|
|**fingerPrint**|String|指纹|
|**createTime**|String|创建时间|
|**updateTime**|String|更新时间|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
