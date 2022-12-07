# describeSnapshot


## 描述
查询云硬盘快照信息详情

## 请求方式
GET

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
|**result**|[Result](#result)|查询的快照信息详情|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**snapshot**|[Snapshot](#snapshot)| |
### <div id="Snapshot">Snapshot</div>
|名称|类型|描述|
|---|---|---|
|**snapshotId**|String|云硬盘快照ID|
|**diskId**|String|创建快照的云硬盘ID(snapshotSource为others时不展示)|
|**snapshotSizeGB**|Integer|快照大小，单位为GiB|
|**name**|String|快照名称|
|**status**|String|快照状态，取值为 creating、available、in-use、deleting、error_create、error_delete 之一|
|**deletable**|Boolean|快照是否可以删除|
|**createTime**|String|创建时间|
|**expireTime**|String|过期删除时间|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
GET
```
- 请求示例
```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots/{snapshotId}' 
      --header 'x-jcloud-pin: **********' 
      --header 'Content-Type: application/json' 
```
- 返回示例
  ```JSON
  {
    "requestId": "oyo9y0pn9j",
    "result": {
        "snapshot": {
            "snapshotId": "snapshot-**********",
            "diskId": "vol-**********",",
            "snapshotSizeGB": 30,
            "name": "openapi-Snapshot-test",
            "status": "available",
            "createTime": "2021-08-11T17:24:21+08:00",
            "expireTime": "",
            "deletable": true
          }
      }
  }
```        

```
