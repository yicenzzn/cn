# describeDisks


## 描述
-   查询您已经创建的云硬盘。
-   filters多个过滤条件之间是逻辑与(AND)，每个条件内部的多个取值是逻辑或(OR)


## 请求方式
GET

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/disks

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**orders**|[OrderItem[]](#orderitem)|False| |排序字段，只支持create_time字段|
|**pageNumber**|Integer|False|1|页码, 默认为1, 取值范围：[1,∞)|
|**pageSize**|Integer|False|20|分页大小，默认为20，取值范围：[10,100]|
|**filters**|[Filter[]](#filter)|False| |diskId - 云硬盘ID，精确匹配，支持多个<br>diskType - 云硬盘类型，精确匹配，支持多个，取值为 ssd.io1,ssd.gp2,ssd.io2<br>status - 云硬盘状态，精确匹配 <br>az - 可用区，精确匹配<br>name - 云硬盘名称，模糊匹配，支持单个<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|
### <div id="OrderItem">OrderItem</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |排序字段。|
|**direction**|Integer|False| |0:升序 1:降序|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeDisks#Result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**disks**|[Disk[]](#disk)|查询的云硬盘信息详情列表|
|**totalCount**|Integer|查询的云硬盘数目|
### <div id="Disk">Disk</div>
|名称|类型|描述|
|---|---|---|
|**diskId**|String|云硬盘ID|
|**az**|String|云硬盘所属AZ|
|**name**|String|云硬盘名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**description**|String|云硬盘描述，允许输入UTF-8编码下的全部字符，不超过256字符。|
|**diskType**|String|云硬盘类型，取值为 ssd.io1,ssd.gp2,ssd.io2|
|**diskSizeGB**|Integer|云硬盘大小，单位为 GiB|
|**iops**|Integer|该云硬盘实际应用的iops值|
|**throughput**|Integer|该云硬盘实际应用的吞吐量的数值|
|**status**|String|云硬盘状态，取值为 creating、available、in-use、extending、restoring、deleting、deleted、error_create、error_delete、error_restore、error_extend、in-recyclebin 之一|
|**attachments**|[DiskAttachment[]](#diskattachment)|挂载信息|
|**snapshotId**|String|创建该云硬盘的快照ID|
|**canRenew**|Boolean|是否可以续费|
|**associateId**|String|关联的主机ID(标识随主机创建的云盘)|
|**createTime**|String|创建云硬盘时间|
|**charge**|[Charge](describeDisks#Charge)|云硬盘计费配置信息|
### <div id="Charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
### <div id="DiskAttachment">DiskAttachment</div>
|名称|类型|描述|
|---|---|---|
|**attachmentId**|String|挂载ID|
|**diskId**|String|云硬盘ID|
|**instanceType**|String|挂载实例的类型，取值为 vm、nc|
|**instanceId**|String|挂载实例的ID|
|**status**|String|挂载状态，取值为 "attaching", "attached", "detaching", "detached"|
|**attachTime**|String|挂载时间|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
GET
```
- 请求示例
#### 示例一: filters为空,返回全部查询个数
```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks' 
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json'
```

#### 示例二: 按多个diskId查询
```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks?filters.1.name=diskId
           &filters.1.values.0=vol-**********&filters.2.name=diskId&filters.2.values.0=vol-**********' 
    --header 'x-jcloud-pin: **********' 
    --header 'Content-Type: application/json'
```

#### 示例三: 组合查询 (az、status、diskType和name)
 ```JSON
curl --location --request GET 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks?filters.1.name=az
           &filters.1.values.0=az1&filters.2.name=status&filters.2.values.0=available
           &filters.3.name=diskType&filters.3.values.0=ssd.io1&filters.4.name=name&filters.4.values.0=openapi-disk-test' 
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
{
   "requestId": "570vr3t592",
   "result": {
   "totalCount": 1,
   "disks": [
     {
         "diskId": "vol-**********",
         "name": "openapi-disk-test",
         "diskSizeGB": 20,
         "diskType": "ssd.io1",
         "iops": 500,
         "throughput": 80,
         "az": "cn-south-1a",
         "status": "available",
         "description": "",
         "snapshotId": "",
         "createTime": "2021-08-11T15:56:10+08:00",
         "attachments": null,
         "charge": {
             "chargeMode": "postpaid_by_duration",
             "chargeStatus": "normal",
             "chargeStartTime": "2021-08-11T07:56:37Z",
             "chargeExpiredTime": "",
             "chargeRetireTime": ""
         },
         "enabled": true,
         "properties": null,
         "flag": 0,
         "canPutInRecycleBin": true,
         "trashTime": "2022-03-22T23:59:59+08:00",
         "resourceGroupId": "rg-default"
     }
   ]
 }
 

```
