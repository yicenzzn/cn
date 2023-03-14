# describeContainers


## 描述
批量查询原生容器的详细信息<br>
此接口支持分页查询，默认每页20条。


## 请求方式
GET

## 请求地址
https://nativecontainer.jdcloud-api.com/v1/regions/{regionId}/containers

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |页码；默认为1|
|**pageSize**|Integer|False| |分页大小；默认为20；取值范围[10, 100]|
|**filters**|[Filter[]](describecontainers#filter)|False| |containerId - 实例ID，精确匹配，支持多个<br>privateIpAddress - 主网卡IP地址，模糊匹配，支持单个<br>az - 可用区，精确匹配，支持多个<br>vpcId - 私有网络ID，精确匹配，支持多个<br>status - 容器状态，精确匹配，支持多个<br>name - 容器名称，模糊匹配，支持单个<br>subnetId - 子网ID，精确匹配，支持多个<br>|
|**tags**|[TagFilter[]](describecontainers#tagfilter)|False| |Tag筛选条件|
|**resourceGroupIds**|String[]|False| |资源组ID|

### <div id="tagfilter">TagFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**values**|String[]|False| |Tag值|
### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describecontainers#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**containers**|[Container[]](describecontainers#container)| |
|**totalCount**|Number| |
### <div id="container">Container</div>
|名称|类型|描述|
|---|---|---|
|**containerId**|String|容器ID|
|**status**|String|容器状态|
|**instanceType**|String|实例类型|
|**az**|String|可用区|
|**name**|String|容器名称|
|**hostAliases**|[HostAlias[]](describecontainers#hostalias)|域名和IP映射的信息|
|**hostname**|String|主机名|
|**command**|String[]|容器执行命令|
|**args**|String[]|容器执行命令的参数|
|**envs**|[EnvVar[]](describecontainers#envvar)|动态指定的容器执行的环境变量|
|**image**|String|镜像名称|
|**secret**|String|镜像仓库认证信息名称|
|**tty**|Boolean|容器是否分配tty|
|**workingDir**|String|容器的工作目录|
|**rootVolume**|[VolumeMount](describecontainers#volumemount)|根Volume信息|
|**dataVolumes**|[VolumeMount[]](describecontainers#volumemount)|挂载的数据Volume信息|
|**vpcId**|String|主网卡所属VPC的ID|
|**subnetId**|String|主网卡所属子网的ID|
|**privateIpAddress**|String|主网卡主IP地址|
|**elasticIpId**|String|主网卡主IP绑定弹性IP的ID|
|**elasticIpAddress**|String|主网卡主IP绑定弹性IP的地址|
|**primaryNetworkInterface**|[InstanceNetworkInterfaceAttachment](describecontainers#instancenetworkinterfaceattachment)|主网卡配置信息|
|**secondaryNetworkInterfaces**|[InstanceNetworkInterfaceAttachment[]](describecontainers#instancenetworkinterfaceattachment)|辅助网卡配置信息|
|**logConfiguration**|[LogConfiguration](describecontainers#logconfiguration)|容器日志配置信息|
|**tags**|[Tag[]](describecontainers#tag)|Tag信息|
|**charge**|[Charge](describecontainers#charge)|计费配置信息|
|**launchTime**|String|创建时间|
|**reason**|String|容器终止原因|
|**description**|String|容器描述|
|**resourceGroupId**|String|资源组ID|

### <div id="charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
### <div id="tag">Tag</div>
|名称|类型|描述|
|---|---|---|
|**key**|String|Tag键|
|**value**|String|Tag值|
### <div id="logconfiguration">LogConfiguration</div>
|名称|类型|描述|
|---|---|---|
|**logDriver**|String|日志Driver名称  default：默认在本地分配10MB的存储空间，自动rotate|
### <div id="instancenetworkinterfaceattachment">InstanceNetworkInterfaceAttachment</div>
|名称|类型|描述|
|---|---|---|
|**autoDelete**|Boolean|指明删除实例时是否删除网卡|
|**deviceIndex**|Integer|设备Index|
|**attachStatus**|String|绑定状态|
|**attachTime**|String|绑定时间|
|**networkInterface**|[InstanceNetworkInterface](describecontainers#instancenetworkinterface)|弹性网卡信息|
### <div id="instancenetworkinterface">InstanceNetworkInterface</div>
|名称|类型|描述|
|---|---|---|
|**networkInterfaceId**|String|弹性网卡ID|
|**macAddress**|String|以太网地址|
|**vpcId**|String|虚拟网络ID|
|**subnetId**|String|子网ID|
|**description**|String|描述|
|**securityGroups**|[SecurityGroupSimple[]](describecontainers#securitygroupsimple)|安全组列表|
|**sanityCheck**|Boolean|源和目标IP地址校验，取值为0或者1|
|**primaryIp**|[NetworkInterfacePrivateIp](describecontainers#networkinterfaceprivateip)|网卡主IP|
|**secondaryIps**|[NetworkInterfacePrivateIp[]](describecontainers#networkinterfaceprivateip)| |
### <div id="networkinterfaceprivateip">NetworkInterfacePrivateIp</div>
|名称|类型|描述|
|---|---|---|
|**privateIpAddress**|String|私有IP的IPV4地址|
|**elasticIpId**|String|弹性IP实例ID|
|**elasticIpAddress**|String|弹性IP实例地址|
### <div id="securitygroupsimple">SecurityGroupSimple</div>
|名称|类型|描述|
|---|---|---|
|**groupId**|String|安全组ID|
|**groupName**|String|安全组名称|
### <div id="volumemount">VolumeMount</div>
|名称|类型|描述|
|---|---|---|
|**category**|String|磁盘分类|
|**autoDelete**|Boolean|自动删除，删除容器时自动删除此volume|
|**mountPath**|String|容器内的挂载目录|
|**readOnly**|Boolean|只读，默认false；只针对data volume有效，root volume为false|
|**cloudDisk**|[InstanceCloudDisk](describecontainers#instanceclouddisk)|云硬盘规格|
|**localDisk**|[InstanceLocalDisk](describecontainers#instancelocaldisk)|云硬盘规格|
|**fsType**|String|指定volume文件系统类型，目前支持[xfs, ext4]|
### <div id="instancelocaldisk">InstanceLocalDisk</div>
|名称|类型|描述|
|---|---|---|
|**diskSize**|Integer|本地盘大小(GB)|
### <div id="instanceclouddisk">InstanceCloudDisk</div>
|名称|类型|描述|
|---|---|---|
|**diskId**|String|云硬盘ID|
|**az**|String|所属AZ|
|**name**|String|硬盘名称|
|**description**|String|硬盘描述|
|**diskType**|String|磁盘类型|
|**diskSize**|Integer|磁盘大小（GiB）|
|**iops**|Integer|用户指定购买的iops值，目前只支持 ssd.io1 类型云盘|
|**status**|String|云硬盘状态，取值为 creating、available、in-use、extending、restoring、deleting、deleted、error_creating、error_deleting、error_restoring、error_extending 之一|
|**createTime**|String|创建时间|
### <div id="envvar">EnvVar</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|环境变量名称|
|**value**|String|环境变量的值|
### <div id="hostalias">HostAlias</div>
|名称|类型|描述|
|---|---|---|
|**hostnames**|String[]|域名列表|
|**ip**|String|IP地址|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
