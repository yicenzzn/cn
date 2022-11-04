# deleteSnapshot


## 描述
-   删除单个云硬盘快照:快照状态必须为 available 或 error 状态。
-   快照独立于云硬盘生命周期，删除快照不会对创建快照的云硬盘有任何影响。
-   快照删除后不可恢复，请谨慎操作。


## 请求方式
DELETE

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/snapshots/{snapshotId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**snapshotId**|String|True| |快照ID|

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

## 请求示例
DELETE
```
- 请求示例
```JSON
curl --location --request DELETE 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots/{snapshotId}' 
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json' 
```
- 返回示例
```JSON
{
  "requestId":"mcqirc8y9t",
}

```
