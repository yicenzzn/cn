# describeInstances


## 描述

查询一台或多台合作云主机实例的详细信息。

详细操作说明请参考帮助文档：[查找实例](https://docs.jdcloud.com/cn/virtual-machines/search-instance)

## 接口说明
- 使用 `filters` 过滤器进行条件筛选，每个 `filter` 之间的关系为逻辑与（AND）的关系。
- 如果使用子帐号查询，只会查询到该子帐号有权限的合作云主机实例。关于资源权限请参考 [IAM概述](https://docs.jdcloud.com/cn/iam/product-overview)。
- 单次查询最大可查询100条合作云主机实例数据。
- 尽量一次调用接口查询多条数据，不建议使用该批量查询接口一次查询一条数据，如果使用不当导致查询过于密集，可能导致网关触发限流。
- 由于该接口为 `GET` 方式请求，最终参数会转换为 `URL` 上的参数，但是 `HTTP` 协议下的 `GET` 请求参数长度是有大小限制的，使用者需要注意参数超长的问题。


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码；默认为1。|
|**pageSize**|Integer|False|20|分页大小；<br>默认为20；取值范围[10, 100]。|
|**filters**|[Filter[]](#filter)|False| |<b>filters 中支持使用以下关键字进行过滤</b><br>`privateIpAddress`: 云主机挂载的网卡内网主IP地址，模糊匹配，支持单个<br>`status`: 云主机状态，精确匹配，支持单个，参考 [云主机状态](https://docs.jdcloud.com/virtual-machines/api/vm_status)<br>`name`: 云主机名称，模糊匹配，支持单个<br>`instanceType`: 实例规格，精确匹配，支持单个，可通过查询 [DescribeInstanceTypes](https://docs.jdcloud.com/virtual-machines/api/describeinstancetypes) 接口获得实例规格。<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instances**|[Instance[]](#instance)|云主机实例列表。|
|**totalCount**|Number|本次查询可匹配到的总记录数，使用者需要结合 `pageNumber` 和 `pageSize` 计算是否可以继续分页。|
### <div id="Instance">Instance</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|云主机ID。|
|**partnerId**|String|合作伙伴主机ID|
|**instanceName**|String|云主机名称。|
|**instanceType**|String|实例规格。|
|**vpcId**|String|主网卡所属VPC的ID。|
|**subnetId**|String|主网卡所属子网的ID。|
|**privateIpAddress**|String|主网卡主内网IP地址。|
|**elasticIpAddress**|String|主网卡主IP绑定弹性IP的地址。|
|**elasticIpId**|String|主网卡主IP绑定弹性IP的ID。|
|**status**|String|云主机状态，参考 [合作云主机状态](https://docs.jdcloud.com/coc-virtual-machines/api/vm_status)。|
|**imageId**|String|云主机使用的镜像ID。|
|**systemDisk**|[InstanceDiskAttachment](#instancediskattachment)|系统盘配置。|
|**dataDisks**|[InstanceDiskAttachment[]](#instancediskattachment)|数据盘配置列表。|
|**primaryNetworkInterface**|[InstanceNetworkInterfaceAttachmentDetail](#instancenetworkinterfaceattachmentdetail)|主网卡主IP关联的弹性公网IP配置。|
|**az**|String|云主机所在可用区。|
|**region**|String|云主机所在地域。|
|**keyName**|String|云主机使用的密钥对名称。|
|**launchTime**|String|创建时间，格式为：YYYY-MM-DD HH:mm:ss|
|**charge**|[Charge](#charge)|云主机的计费信息。|
### <div id="Charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prePaid表示预付费，默认为prePaid|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
### <div id="InstanceNetworkInterfaceAttachmentDetail">InstanceNetworkInterfaceAttachmentDetail</div>
|名称|类型|描述|
|---|---|---|
|**vpcId**|String|弹性网卡所属VPC的ID。|
|**subnetId**|String|子网ID。|
|**securityGroups**|[SecurityGroupSimple[]](#securitygroupsimple)| |
|**ip**|String|私有IP的IPV4地址|
|**portId**|String|弹性网卡ID。|
### <div id="SecurityGroupSimple">SecurityGroupSimple</div>
|名称|类型|描述|
|---|---|---|
|**groupId**|String|安全组ID。|
|**groupName**|String|安全组名称。|
### <div id="InstanceDiskAttachment">InstanceDiskAttachment</div>
|名称|类型|描述|
|---|---|---|
|**diskId**|String|云盘ID。<br>|
|**deviceName**|String|磁盘逻辑挂载点。<br>**系统盘**：默认为vda。<br>**数据盘**：取值范围：`[vdb~vdbm]`。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|OUT_OF_RANGE|PageSize out of range|分页大小超出规定范围。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET

```
/v1/regions/cn-north-1/instances?pageNumber=1&pageSize=10&filters.1.name=instanceId&filters.1.values.1=i-eumm****d6&filters.1.values.2=i-y5nh****9w
```


## 返回示例
```
{
    "requestId": "e822b1613bde0dac45596cf756e9c37b", 
    "result": {
        "instances": [
            {
                "az": "cn-north-1c", 
                "charge": {
                    "chargeMode": "postpaid_by_duration", 
                    "chargeStartTime": "2021-07-19T12:33:17Z", 
                    "chargeStatus": "normal"
                }, 
                "hostName": "test1", 
                "imageId": "img-m5s0****29", 
                "instanceId": "i-eumm****d6", 
                "instanceName": "test1", 
                "instanceType": "g.n2.large", 
                "launchTime": "2021-07-19 20:33:17", 
                "primaryNetworkInterface": {
                    "privateIpAddress": [
                        "127.0.0.1"
                    ], 
                    "securityGroupsIds": [
                        {
                            "groupId": "sg-p2d1****ya", 
                            "groupName": "sfewfwe"
                        }
                    ], 
                    "subnetId": "subnet-c2p3****9o", 
                    "vpcId": "vpc-z9r3****p8"
                }, 
                "privateIpAddress": "127.0.0.1", 
                "status": "stopped", 
                "subnetId": "subnet-c2p3****9o", 
                "systemDisk": {
                    "autoDelete": true, 
                    "deviceName": "vda", 
                    "diskId": "vol-u8r2****c1"
                }, 
                "vpcId": "vpc-z9r3****p8"
            }, 
            {
                "az": "cn-north-1c", 
                "charge": {
                    "chargeMode": "postpaid_by_duration", 
                    "chargeStartTime": "2021-07-19T12:33:17Z", 
                    "chargeStatus": "normal"
                }, 
                "hostName": "test2", 
                "imageId": "img-m5s0****59", 
                "instanceId": "i-eumm****d2", 
                "instanceName": "test2", 
                "instanceType": "g.n2.large", 
                "launchTime": "2021-07-19 20:33:17", 
                "primaryNetworkInterface": {
                    "privateIpAddress": [
                        "127.0.0.1"
                    ], 
                    "securityGroupsIds": [
                        {
                            "groupId": "sg-p2d1****ya", 
                            "groupName": "sfewfwe"
                        }
                    ], 
                    "subnetId": "subnet-c2p3****9o", 
                    "vpcId": "vpc-z9r3****p8"
                }, 
                "privateIpAddress": "127.0.0.1", 
                "status": "stopped", 
                "subnetId": "subnet-c2p3****9o", 
                "systemDisk": {
                    "autoDelete": true, 
                    "deviceName": "vda", 
                    "diskId": "vol-u8r2****c1"
                }, 
                "vpcId": "vpc-z9r3****p8"
            }
        ], 
        "totalCount": 2
    }
}
```
