# modifyDiskAttribute


## 描述
修改云硬盘的名字或描述信息，名字或描述信息至少要指定一个。

## 请求方式
PATCH

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/disks/{diskId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**diskId**|String|True| |云硬盘ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |云硬盘名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**description**|String|False| |云硬盘描述，允许输入UTF-8编码下的全部字符，不超过256字符。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|请求id|


## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
PATCH
```
#### 示例一: name为缺省值，默认name为disk原有name值
- 请求示例
```JSON
curl --location --request PATCH 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks/{diskId}' 
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json' 
    --data '{
        "description":"this is a demo for modifydisk"
      }'
```
- 返回示例
```JSON
{
  "requestId":"rbinzj36bg",
}


#### 示例二: 修改name值
```JSON
curl --location --request PATCH 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks/{diskId}' 
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json' 
    --data '{
        "name":"openapi-disk-test—modify"
      }'
```
- 返回示例
```JSON
{
  "requestId":"4u8j6ajxar",
}

```
