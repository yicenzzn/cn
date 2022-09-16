# stopReplication


## 描述
暂停指定的复制任务。注意：如果暂停的时间过长，会导致 TiCDC 节点的磁盘空间写满，导致复制任务错误或失败。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/replications/{taskId}:stopReplication

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|
|**taskId**|String|True| |复制任务ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
