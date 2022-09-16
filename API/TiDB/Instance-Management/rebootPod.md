# rebootPod


## 描述
重启实例的某类节点。重启采用滚动重启的方式，如果该类节点有多个，通常不会中断实例的服务。

## 请求方式
POST

## 请求地址
https://tidb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:rebootpod

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**nodeType**|String[]|True| |重启指定类型的pod,支持Tikv,TiDB,PD,TiFlash|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**202**|OK|
