# describeSnapshots


## 描述
查询云硬盘快照列表，filters多个过滤条件之间是逻辑与(AND)，每个条件内部的多个取值是逻辑或(OR)

## 请求方式
GET

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/snapshots

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](#filter)|False| |snapshotId - 云硬盘快照ID<br>diskId - 生成快照的云硬盘ID<br>status - 快照状态，精确匹配，单个匹配，多个取第一个，取值为 creating、available、deleting、error_create、error_delete<br>name - 快照名称，精确匹配，支持单个<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**snapshots**|[Snapshot[]](#snapshot)|查询的快照信息详情列表|
|**totalCount**|Integer|查询的快照数目|
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
#### 示例一: filters,返回全部查询个数
```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots' 
      --header 'x-jcloud-pin: **********' 
      --header 'Content-Type: application/json' 
```

#### 示例二: 按多个snapshotId查询
```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots?filters.1.name=snapshotId
            &filters.1.values.0=Snapshot-**********&filters.2.name=snapshotId&filters.2.values.0=Snapshot-**********' 
     --header 'x-jcloud-pin: **********' 
     --header 'Content-Type: application/json'

```

#### 示例三: 组合查询(status和name)
```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/snapshots?filters.1.name=status
            &filters.1.values.0=available&filters.2.name=name&filters.2.values.0=openapi-Snapshot-test' 
     --header 'x-jcloud-pin: **********' 
     --header 'Content-Type: application/json'
```

- 返回示例
#### 如按查询条件查询失败，则返回如下：
```JSON
 {
    "requestId": "18c5027iys",
    "result": {
        "totalCount": 0,
        "disks": null
    }
 }
```
#### 若按上述请求示例三查询成功，则返回如下：
```JSON
{
  "requestId": "j17dvyzh01",
  "result": {
      "totalCount": 1,
      "snapshots": [
          {
            "snapshotId": "snapshot-**********",
            "diskId": "vol-**********",
            "snapshotSizeGB": 30,
            "name": "openapi-Snapshot-test",
            "status": "available",
            "createTime": "2021-08-11T17:24:21+08:00",
            "expireTime": "",
            "deletable": true                    
          }
      ]
  }
}
```

```
