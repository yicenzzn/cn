# restoreDisk


## 描述
-   仅可对制作快照的源硬盘进行数据恢复操作。
-   仅源硬盘处于可用状态时才能使用快照进行数据恢复操作。
-   云硬盘恢复后，当前数据将被清除，请您谨慎操作。


## 请求方式
POST

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}:restore

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**diskId**|String|True| |云硬盘ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**snapshotId**|String|True| |用于恢复云盘的快照ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
POST
```
- 请求示例
```JSON
curl --location --request PATCH 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks/{diskId}:restore' 
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json' 
    --data '{
        "snapshotId":"snapshot-**********"
      }'
```
- 返回示例
```JSON
{
    "requestId": "6ckpixh75n"
}
```

```
