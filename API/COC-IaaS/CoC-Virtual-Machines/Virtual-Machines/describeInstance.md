# describeInstance


## 描述

查询一台合作云主机实例的详细信息。

详细操作说明请参考帮助文档：[查找实例](https://docs.jdcloud.com/cn/coc-virtual-machines/search-instance)

## 接口说明
- 该接口与查询云主机列表返回的信息一致。
- 只需要查询单个云主机实例详细信息的时候可以调用该接口。


## 请求方式
GET

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|
|**instanceId**|String|True| |合作云主机ID。|

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
|**instance**|[Instance](#instance)| |
### <div id="Instance">Instance</div>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|云主机ID。|
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
|**404**|NOT_FOUND|Instance 'xx' not found.|云主机实例不存在。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET

```
/v1/regions/cn-north-1/instances/i-eumm****d6
```


## 返回示例
```
{
    "requestId": "f2cbc5b286209ebe6629016a3d90dad8", 
    "result": {
        "instance": {
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
    }
}
```
