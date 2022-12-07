# createInstances


## 描述

创建一台或多台指定配置的合作云主机实例。

详细操作说明请参考帮助文档：[创建实例](https://docs.jdcloud.com/cn/coc-virtual-machines/create-instance)

## 接口说明
- 创建实例前，请参考 [创建前准备](https://docs.jdcloud.com/coc-virtual-machines/account-preparation-linux) 完成实名认证、支付方式确认、计费类型选择等准备工作。
- 创建实例的配置说明和选择指导，请参考 [配置项说明](https://docs.jdcloud.com/cn/coc-virtual-machines/select-configuration-linux)。
- 各地域下实例及关联资源（合作云硬盘、合作弹性公网IP）的可创建数量受配额限制，创建前请通过 [DescribeUsage](https://docs.jdcloud.com/cn/coc-virtual-machines/api/describeusage?content=API) 确认配额，如须提升请[提交工单](https://ticket.jdcloud.com/applyorder/submit)或联系京东云客服。
- 不同地域及可用区下售卖的实例规格有差异，可通过 [DescribeInstanceTypes](https://docs.jdcloud.com/coc-virtual-machines/api/describeinstancetypes?content=API) 查询在售规格及规格详细信息。
- 通过本接口创建包年包月实例时将自动从账户扣款（代金券优先），如需使用第三方支付方式请通过控制台创建。
- 单次请求最多支持创建 `100` 台实例。
- 本接口为异步接口，请求下发成功后会返回RequestId和实例ID，此时实例处于 `Pending`（创建中）状态。如创建成功则实例自动变为 `Running`（运行中）状态；如创建失败则短暂处于 `Error`（错误）状态，随后将自动删除（创建失败的实例不会收费且会自动释放占用的配额）。实例状态可以通过 [describeInstanceStatus](https://docs.jdcloud.com/coc-virtual-machines/api/describeinstancestatus?content=API) 接口查询。
- 批量创建多台实例时系统将尽可能完成目标创建数量，但受底层资源、配额等因素影响，可能存在部分成功部分失败的情况，还请关注最终完成数量，如有失败情况请尝试重新申请或联系客服。


## 请求方式
POST

## 请求地址
https://coc-vm.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceSpec**|[InstanceSpec](#instancespec)|True| |实例配置。<br>|
|**maxCount**|Integer|False|1|创建实例的数量，不能超过用户配额。<br>取值范围：[1,100]；默认值：1。<br>如果在弹性网卡中指定了内网IP地址，那么单次创建 `maxCount` 只能是 1。<br>|
|**clientToken**|String|False| |用于保证请求的幂等性。由客户端生成，并确保不同请求中该参数唯一，长度不能超过64个字符。<br>|

### <div id="InstanceSpec">InstanceSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |实例所属的可用区。<br>|
|**instanceType**|String|True| |实例规格。可通过 [DescribeInstanceTypes](https://docs.jdcloud.com/coc-virtual-machines/api/describeinstancetypes) 接口查询各地域及可用区下的规格售卖情况。<br>|
|**imageId**|String|True| |镜像ID。可通过 [DescribeImages](https://docs.jdcloud.com/coc-virtual-machines/api/describeimages) 接口获得指定地域的镜像信息。<br>|
|**name**|String|True| |实例名称。长度为1~64字符，可以包含中文、数字、大小写字母、英文下划线“_”、中划线“-”或点“.”,，不能以“.”作为首尾。<br>|
|**password**|String|False| |实例密码。可用于SSH登录和VNC登录。长度8至26字符，至少包含以下三项：1.数字：0~9；2.小写字母：a~z；3.大写字母：A~Z，或特殊字符：(!@$%^-_=+[{}]:,./?)。不可包含连续数字，例如123、987；不可包含连续或键位连续字母，如abc、CBA、qaz、qwer；不可包含用户名"Administrator" 和“root”及逆序字符，不可包含用户名"Administrator" 中超过两个连续字符的部分，更多密码输入要求请参见 [公共参数规范](https://docs.jdcloud.com/virtual-machines/api/general_parameters)。<br>|
|**keyName**|String|False| |密钥对名称。仅Linux系统下该参数生效，当前仅支持输入单个密钥，password和keyName只能二选一。passwordAuth不为yes的情况下，密钥对名称不能为空。<br>|
|**passwordAuth**|String|False| |是否允许SSH密码登录，默认为yes；yes：允许SSH密码登录。no：禁止SSH密码登录，这时必须要传keyName。该参数值为yes时，可以不传password，这时自动生成随机密码，并以短信和邮件通知。<br>|
|**elasticIpSpec**|[ElasticIpSpec](#elasticipspec)|False| |弹性公网IP配置<br>|
|**primaryNetworkInterface**|[NetworkInterfaceSpec](#networkinterfacespec)|True| |主网卡配置。<br>|
|**systemDisk**|[InstanceDiskAttachmentSpec](#instancediskattachmentspec)|True| |系统盘配置。<br>|
|**dataDisks**|[InstanceDiskAttachmentSpec[]](#instancediskattachmentspec)|False| |数据盘配置。单实例最多可挂载云硬盘（系统盘+数据盘）的数量受实例规格的限制。<br>|
|**charge**|[ChargeSpec](#chargespec)|False| |计费配置。<br>云主机不支持按用量方式计费，如果计费配置为空，则按照包年包月计费方式处理。<br>打包创建数据盘的情况下，数据盘的计费方式只能与云主机保持一致。<br>打包创建弹性公网IP的情况下，若公网IP的计费方式没有指定为按用量计费，那么公网IP计费方式只能与云主机保持一致。<br>|
### <div id="ChargeSpec">ChargeSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**chargeMode**|String|False|prepaid_by_duration|计费模式，取值为：prepaid_by_duration 表示预付费|
|**chargeUnit**|String|False| |预付费计费单位，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month|
|**chargeDuration**|Integer|False| |预付费计费时长，当chargeMode取值为prepaid_by_duration时有效。默认取值1。当chargeUnit为month时取值范围：[1-9]，当chargeUnit为year时取值范围：[1-3]|
|**autoRenew**|Boolean|False| |是否自动续费，默认否|
### <div id="InstanceDiskAttachmentSpec">InstanceDiskAttachmentSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**diskType**|String|True| |云硬盘类型。<br>|
|**diskSizeGB**|Integer|False| |云硬盘大小，单位为 GiB。<br>|
### <div id="NetworkInterfaceSpec">NetworkInterfaceSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**vpcId**|String|True| |VPC ID|
|**subnetId**|String|True| |子网ID|
|**ip**|String|False| |网卡主IP，如果不指定，会自动从子网中分配|
|**securityGroups**|[SecurityGroupCreate[]](#securitygroupcreate)|True| | |
### <div id="SecurityGroupCreate">SecurityGroupCreate</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**groupId**|String|True| |安全组ID。|
|**groupName**|String|False| |安全组名称。|
### <div id="ElasticIpSpec">ElasticIpSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**sizeMbps**|Integer|True| |弹性公网IP的带宽上限，单位：Mbps。取值范围为：[1-200]|
|**provider**|String|True| |弹性公网IP线路，目前仅支持bgp，|
|**chargeMode**|String|False| |弹性公网IP计费模式，目前仅支持prepaid_by_duration（包年包月），默认值prepaid_by_duration，计费模式同实例计费模式。|
|**chargePlan**|String|False| |弹性公网IP带宽计费模式，目前仅支持bandwidth（按带宽），默认值为bandwidth|
|**chargeUnit**|String|False| |预付费计费单位，当chargeMode为prepaid_by_duration时有效，取值为：month、year，默认为month，计费单位同实例计费单位。|
|**chargeDuration**|Integer|False| |预付费计费时长，当chargeMode取值为prepaid_by_duration时有效。默认取值1。当chargeUnit为month时取值范围：[1-9]，当chargeUnit为year时取值范围：[1-3]，计费时长同实例计费时长。|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**instanceIds**|String[]|实例ID列表。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**400**|INVALID_ARGUMENT|Parameter InstanceSpec.ImageId missing|参数ImageId不可为空。|
|**400**|INVALID_ARGUMENT|Invalid password|密码不符合规范。|
|**400**|FAILED_PRECONDITION|Disk type 'xx' is out of stock|“xx”类型云硬盘已售罄。|
|**400**|FAILED_PRECONDITION|Image 'xx' not ready|所选镜像“xx”处于非可用状态。|
|**400**|FAILED_PRECONDITION|Image constraints. Doesn't support instanceType 'xx'|所选镜像不支持当前配置的实例规格'xx'。|
|**400**|OUT_OF_RANGE|Maxcount out of range|创建数量超过允许上限。|
|**400**|OUT_OF_RANGE|InstanceSpec.SystemDisk.CloudDiskSpec.DiskSizeGB out of range|系统盘容量超出允许范围。|
|**400**|CONFLICT|Subnet 'xx' not support ipv6|所选子网不支持IPv6。|
|**404**|NOT_FOUND|InstanceType 'xx' not found|实例规格不存在。|
|**404**|NOT_FOUND|Subnet 'xx' not found|子网不存在。|
|**404**|NOT_FOUND|SecurityGroups 'xx' not found|安全组不存在。|
|**404**|NOT_FOUND|KeyPair 'xx' not found|密钥不存在。|
|**404**|NOT_FOUND|Image 'xx' not found|镜像不存在。|
|**429**|QUOTA_EXCEEDED|Instance quota limit exceeded|云主机配额不足。|
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
POST

调用方法、签名算法及公共请求参数请参考 [京东云OpenAPI公共说明](https://docs.jdcloud.com/common-declaration/api/introduction)。

中国-香港可用区A，创建1台 `g.n2.large` 规格的包月计费实例，包月时长1个月，设置 `密码` ，创建并绑定5Mbps的 `BGP IP`，系统盘类型指定为 `通用型SSD`，随实例创建一块20GB的 `性能型SSD` 。

- 请求示例

```
/v1/regions/cn-north-1/instances
{
  "maxCount":1,
  "InstanceSpec":{
    "az":"cn-north-1a",
    "ImageId":"img-m5s0****29",
    "InstanceType":"g.n2.large",
    "name":"instance",
    "password":"A1i2n@Apix#",
    "charge":{
      "chargeMode":"prepaid_by_duration",
      "chargeUnit":"month",
      "chargeDuration":1
    }
    "primaryNetworkInterface":{
      "networkInterface":{
        "subnetId":"subnet-c2p3****9o",
        "securityGroups":[
          "sg-p2d1****ya"
        ]
      }
    },
    "systemDisk":{
      "diskType":"ssd.gp1",
      "diskSizeGB":100
    },
    "dataDisks":[
    {
      "diskType":"ssd.gp1",
       "diskSizeGB":100
      }
    }
    ]
  }
}
```

- 返回示例

```
{
  "result":{
    "instanceIds":[
      "i-eumm****d6"
    ]
  },
  "requestId":"c2i8w4g6fiqocr2fetqf8ef59k1k4wir"
}
```


