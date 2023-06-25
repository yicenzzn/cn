# reinstallInstance


## 描述
重装分布式云物理服务器，只能重装stopped状态的服务器<br/>
- 可调用接口（describeOS）获取分布式云物理服务器支持的操作系统列表
<br>敏感操作，可开启<a href="https://docs.jdcloud.com/cn/security-operation-protection/operation-protection">MFA操作保护</a>

## 请求方式
PUT

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:reinstallInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|
|**instanceId**|String|True| |分布式云物理服务器ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**clientToken**|String|False| |由客户端生成，用于保证请求的幂等性，长度不能超过36个字符；<br/><br>如果多个请求使用了相同的clientToken，只会执行第一个请求，之后的请求直接返回第一个请求的结果<br/><br>|
|**instanceSpec**|[ReinstallInstanceSpec](#reinstallinstancespec)|True| |分布式云物理服务器配置|

### <div id="ReinstallInstanceSpec">ReinstallInstanceSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|True| |可用区, 如cn-east-tz1a|
|**imageType**|String|True| |镜像类型, 取值范围：standard|
|**osTypeId**|String|True| |操作系统类型ID|
|**sysRaidTypeId**|String|True| |系统盘RAID类型ID|
|**keepData**|String|True| |是否保留数据盘数据, 取值为：yes、no|
|**dataRaidTypeId**|String|True| |数据盘RAID类型ID|
|**password**|String|True| |密码|
|**hostname**|String|False| |主机名|
|**userData**|String|False| |可执行脚本Base64编码后的内容，支持shell和python脚本|
|**keypairId**|String|False| |密钥对id|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean|重装操作是否成功|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
