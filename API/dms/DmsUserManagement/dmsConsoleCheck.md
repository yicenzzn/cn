# dmsConsoleCheck


## 描述
校验当前的用户是否允许访问DMS控制台

## 请求方式
GET

## 请求地址
https://dms.jdcloud-api.com/v1/console:check


## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|[String](#result)|请求id|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**strResult**|String|允许访问|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
