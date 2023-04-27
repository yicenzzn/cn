# describeSnapshotsCapacity


## 描述
查询快照容量

## 请求方式
GET

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/snapshots:capacity

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeSnapshotsCapacity#Result)|结果|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**capacities**|[SnapshotCapacity[]](describeSnapshotsCapacity#SnapshotCapacity)| |
### <div id="SnapshotCapacity">SnapshotCapacity</div>
|名称|类型|描述|
|---|---|---|
|**region**|String|区域ID|
|**snapshotCount**|Integer|快照个数|
|**totalSize**|Integer|快照总大小，单位：MB|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
GET
```
- 请求示例
  ```JSON
  curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots:capacity' 
      --header 'x-jcloud-pin: **********' 
      --header 'Content-Type: application/json' 
  ```
  - 返回示例
  ```JSON
  {
    "requestId": "gg6geuheva",
    "result": {
        "capacities": [
            {
                "region": "cn-east-1",
                "snapshotCount": 0,
                "totalSize": 0
            },
            {
                "region": "cn-east-2",
                "snapshotCount": 1,
                "totalSize": 0
            },
            {
                "region": "cn-north-1",
                "snapshotCount": 3,
                "totalSize": 4
            },
            {
                "region": "cn-south-1",
                "snapshotCount": 1,
                "totalSize": 0
            }
          ]
       }
  }
  ```          

```
