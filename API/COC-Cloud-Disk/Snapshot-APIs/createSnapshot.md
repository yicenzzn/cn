# createSnapshot


## 描述
-   为指定云硬盘创建快照，新生成的快照的状态为creating。
-   同一地域下单用户快照的配额为15块。
-   为保证数据完整性，请您在创建快照之前，停止对云硬盘进行写入操作，以保证快照数据的完整性。
-   在执行创建快照前，建议您对云硬盘进行卸载操作，创建快照后再重新挂载到云主机上。
-   手动快照的生命周期独立于云硬盘，请您及时删除不需要的快照。
-   创建快照所需时间取决于云硬盘容量的大小，云硬盘容量越大耗时越长。


## 请求方式
POST

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/snapshots

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**snapshotSpec**|[SnapshotSpec](createSnapshot#SnapshotSpec)|True| |创建快照规格|
|**clientToken**|String|True| |幂等性校验参数|

### <div id="SnapshotSpec">SnapshotSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |快照名称|
|**description**|String|False| |快照描述,默认为空|
|**diskId**|String|True| |用于创建快照的云盘ID|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createSnapshot#Result)|结果集|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**snapshotId**|String|创建的快照ID|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
POST
```
- 请求示例
```JSON
curl --location --request POST 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots' 
      --header 'x-jcloud-pin: **********' 
      --header 'Content-Type: application/json' 
      --data '{
           "snapshotSpec": {
              "name": "openapi-Snapshot-test",
              "diskId": "vol-**********"
            },
            "clientToken": "Snapshot-123456789"
        }'   
```
- 返回示例
  ```JSON
  {
    "requestId": "x3ywxk1jbb",
    "result": {
        "snapshotId": "snapshot-**********""
      }
  }
```

```
