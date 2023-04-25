# describeImages


## 描述

查询镜像信息列表。

详细操作说明请参考帮助文档：[镜像概述](https://docs.jdcloud.com/cn/virtual-machines/image-overview)

## 接口说明
- 通过此接口可以查询到京东云COC系列镜像。
- 请求参数即过滤条件，每个条件之间的关系为逻辑与（AND）的关系。
- 单次查询最大可查询100条镜像信息。
- 尽量一次调用接口查询多条数据，不建议使用该批量查询接口一次查询一条数据，如果使用不当导致查询过于密集，可能导致网关触发限流。
- 由于该接口为 `GET` 方式请求，最终参数会转换为 `URL` 上的参数，但是 `HTTP` 协议下的 `GET` 请求参数长度是有大小限制的，使用者需要注意参数超长的问题。


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/images

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**imageSource**|String|False| |镜像来源，如果没有指定 `ids` 参数，此参数必传。取值范围：<br>`public`：公共镜像。<br>`private`：用户自己的私有镜像。<br>`shared`：共享的镜像。目前暂不支持<br>|
|**platform**|String|False| |根据镜像的操作系统发行版查询。<br>取值范围：`Ubuntu、CentOS、Windows Server、Debian、OpenSUSE、CoreOS、Fedora`。<br>|
|**ids**|String[]|False| |指定镜像ID查询，支持多个，如果指定了此参数，其它参数可以不传。<br>|
|**imageName**|String|False| |根据镜像名称精确查询。|
|**architecture**|String|False| |CPU架构。支持范围：x86_64,arm64。|
|**pageNumber**|Integer|False|1|页码；默认为1。|
|**pageSize**|Integer|False| |分页大小；<br>默认为20；取值范围[10, 100]。|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describeImages#Result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**images**|[Image[]](describeImages#Image)|镜像列表。|
|**totalCount**|Integer|本次查询可匹配到的总记录数，使用者需要结合 `pageNumber` 和 `pageSize` 计算是否可以继续分页。|
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
|**400**|FAILED_PRECONDITION|Parameter ImageSource missing|未指定 imageSource 参数。|
|**400**|OUT_OF_RANGE|PageSize out of range|分页大小超出规定范围。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET
```
```
/v1/regions/cn-hongkong-11/images?ids.1=img-oid1xpptay10&ids.2=img-xwlp8imkej10
```

```

## 返回示例
```
{
    "requestId": "5dfbb22e5f44a6798476bc2408c3bb68", 
    "result": {
        "images": [
            {
                "architecture": "x86_64", 
                "createTime": "2021-01-28 16:49:05", 
                "desc": "", 
                "imageId": "img-m5s0****29", 
                "imageSource": "public", 
                "name": "CentOS 8.2 64位", 
                "osType": "linux", 
                "ownerPin": "admin", 
                "platform": "CentOS", 
                "sizeMB": 2494, 
                "status": "ready", 
                "systemDiskSizeGB": 40
            }, 
            {
                "architecture": "x86_64", 
                "createTime": "2019-12-30 11:05:02", 
                "desc": "", 
                "imageId": "img-m5s0****30", 
                "imageSource": "public", 
                "name": "CentOS 7.6 64位", 
                "osType": "linux", 
                "ownerPin": "admin", 
                "platform": "CentOS", 
                "sizeMB": 0, 
                "status": "ready", 
                "systemDiskSizeGB": 40
            }
        ], 
        "totalCount": 2
    }
}
```
