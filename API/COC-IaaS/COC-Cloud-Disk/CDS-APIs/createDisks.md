# createDisks


## 描述
-   创建一块或多块按配置或者按使用时长付费的云硬盘。
-   云硬盘类型包括增强型SSD(ssd.io2)、第二代通用型SSD(ssd.gp2)、性能型SSD(ssd.io1)。
-   计费方式默认为按配置付费。
-   创建完成后，云硬盘状态为 available。
-   可选参数快照 ID用于从快照创建新盘。
-   批量创建时，云硬盘的命名为 硬盘名称-数字，例如 myDisk-1，myDisk-2。
-   maxCount为最大努力，不保证一定能达到maxCount。


## 请求方式
POST

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/disks

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskSpec**|[DiskSpec](#diskspec)|True| |创建云硬盘规格|
|**maxCount**|Integer|True| |购买实例数量；取值范围：[1,100]|
|**clientToken**|String|True| |幂等性校验参数|

### <div id="DiskSpec">DiskSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |云硬盘所属的可用区|
|**name**|String|True| |云硬盘名称|
|**description**|String|False| |云硬盘描述,默认为空|
|**diskType**|String|True| |云硬盘类型，取值为ssd.io1、ssd.gp2、ssd.io2之一|
|**diskSizeGB**|Integer|True| |云硬盘大小，单位为 GiB，ssd 类型取值范围[20,1000]GB，步长为10G，premium-hdd 类型取值范围[20,3000]GB，步长为10G, ssd.gp2, ssd.io1, ssd.io2 类型取值均是范围[20,16000]GB，步长为10G|
|**iops**|Integer|False|30|云硬盘IOPS的大小，当且仅当云盘类型是ssd.io1型的云盘有效，步长是10.默认值为容量30，最大值为容量50|
|**snapshotId**|String|False| |用于创建云硬盘的快照ID，默认为空|
|**charge**|[ChargeSpec](#chargespec)|False| |计费配置；如不指定，默认计费类型是后付费-按使用时常付费|
### <div id="ChargeSpec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|postpaid_by_duration|计费模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration.请参阅具体产品线帮助文档确认该产品线支持的计费类型|
|**chargeUnit**|String|False| |预付费计费单位，预付费必填，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，预付费必填，当chargeMode取值为prepaid_by_duration时有效。当chargeUnit为month时取值为：1~9，当chargeUnit为year时取值为：1、2、3|
|**autoRenew**|Boolean|False| |True=：OPEN——开通自动续费、False=CLOSE—— 不开通自动续费，默认为CLOSEtrue，为开通自动续费，false为不开通自动续费，仅对包年包月资源有效。开通后，将以本次创建时的购买时长作为自动续费周期，自动续费周期可在续费管理功能中进行修改。|
|**buyScenario**|String|False| |产品线统一活动凭证JSON字符串，需要BASE64编码，目前要求编码前格式为 {"activity":{"activityType":必填字段, "activityIdentifier":必填字段}}|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|结果集|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**diskIds**|String[]|创建的云硬盘ID列表|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
POST
```

#### 示例一: 默认值
- 请求示例
```JSON
 curl --location --request POST 'https://cocdisk.jdcloud-api.com/v1/regions/cn-north-1/disks' 
     --header 'x-jcloud-pin: **********' 
     --header 'Content-Type: application/json' 
     --data '{
          "diskSpec": {
             "az": "{regionId}",
             "name": "openapi-disk-test",
             "diskType": "ssd.io1",
             "diskSizeGB": 20
           },
           "maxCount": 1,
           "clientToken": "volume-clientTok-123456789"
       }'
 ```

 - 返回示例
 ```JSON
 {
   "requestId": "k39b5hri3d",
   "result": {
       "diskIds": [
           "vol-**********"
       ]
    }
 }
 ```

```
