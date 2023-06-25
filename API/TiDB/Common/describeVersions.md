# describeVersions


## 描述
查询指定地域下 TiDB 服务支持的数据库版本

## 请求方式
GET

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/versions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeversions#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**versions**|String[]|TiDB 实例能够提供的所有版本，比如4.0|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
