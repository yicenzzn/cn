# describeImage


## 描述
查询镜像详情。


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/images/{imageId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**imageId**|String|True| |镜像ID。|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**image**|[Image](#image)|镜像信息。|
### <div id="Image">Image</div>
|名称|类型|描述|
|---|---|---|
|**imageId**|String|镜像ID。|
|**partnerImageId**|String|第三方镜像ID。|
|**name**|String|镜像名称。|
|**platform**|String|镜像的操作系统平台名称。<br>取值范围：`Ubuntu、CentOS、Windows Server、Other Linux、Other Windows`。<br>|
|**architecture**|String|CPU架构。支持范围：x86_64。|
|**systemDiskSizeGB**|Integer|镜像系统盘大小。|
|**imageSource**|String|镜像来源，取值范围：<br>`public`：官方镜像。<br>`thirdparty`：镜像市场镜像。<br>`private`：用户自己的私有镜像。<br>`shared`：其他用户分享的镜像。<br>`community`：社区镜像。<br>|
|**osType**|String|镜像的操作系统类型。取值范围：`windows、linux`。|
|**status**|String|镜像状态。参考 [镜像状态](https://docs.jdcloud.com/virtual-machines/api/image_status)。|
|**createTime**|String|镜像的创建时间。|
|**desc**|String|镜像描述。|
|**ownerPin**|String|该镜像拥有者的用户PIN。|
|**snapshots**|[Snapshots[]](#snapshots)|私有镜像关联快照信息|
### <div id="Snapshots">Snapshots</div>
|名称|类型|描述|
|---|---|---|
|**diskSnapshotId**|String|磁盘快照ID。|
|**diskSnapshotName**|String|磁盘快照名称。|
|**diskSize**|Integer|磁盘容量，单位GB。|
|**diskCategory**|String|磁盘类型：系统盘(system_disk)，数据盘(data_disk)|
|**diskType**|String|云硬盘规格。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET
```
```
/v1/regions/cn-north-1/images/img-m5s0****29
```

```

## 返回示例
```
{
    "requestId": "0d1531eb5016b64d801a9e24bac779e8", 
    "result": {
        "image": {
            "architecture": "x86_64", 
            "createTime": "2021-01-28 16:49:05", 
            "desc": "", 
            "imageId": "img-m5s0****29", 
            "imageSource": "public", 
            "name": "CentOS 8.2 64位", 
            "osType": "linux", 
            "ownerPin": "admin", 
            "platform": "CentOS", 
            "status": "ready", 
            "systemDiskSizeGB": 40
        }
    }
}
```
