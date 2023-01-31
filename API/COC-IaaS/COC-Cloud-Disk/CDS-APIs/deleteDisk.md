# deleteDisk


## 描述
-   删除一块按配置计费的云硬盘，云盘类型包括高效云盘、SSD云盘、通用型SSD、性能型SSD和容量型HDD。
-   删除云盘时，云盘的状态必须为 待挂载（Available）。
-   云盘被删除后，云硬盘快照可以被保留。


## 请求方式
DELETE

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**diskId**|String|True| |云硬盘ID|

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
curl --location --request DELETE 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks/{diskId}'  
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json'
```

- 返回示例
```JSON
{
  "requestId": "7ssbq15p3w"
}
```

```
