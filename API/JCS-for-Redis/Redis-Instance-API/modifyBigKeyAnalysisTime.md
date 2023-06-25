# modifyBigKeyAnalysisTime


## 描述
设置大key自动缓存分析时间

## 请求方式
POST

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}/bigKeyAutoAnalysisTime

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前有华北-北京、华南-广州、华东-上海三个区域，Region ID分别为cn-north-1、cn-south-1、cn-east-2|
|**cacheInstanceId**|String|True| |缓存Redis实例ID，是访问实例的唯一标识|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**analysisTime**|String|True| |-表示关闭，否则为：HH:mm-HH:mm 时区，例如"01:00-02:00 +0800"，表示东八区的1点到2点|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|本次请求的ID|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
