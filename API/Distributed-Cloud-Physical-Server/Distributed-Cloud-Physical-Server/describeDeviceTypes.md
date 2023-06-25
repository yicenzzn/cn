# describeDeviceTypes


## 描述
查询分布式云物理服务器实例类型

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/deviceTypes

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeEdCPSRegions）获取分布式云物理服务器支持的地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|False| |可用区，精确匹配|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**deviceTypes**|[DeviceType[]](#devicetype)| |
### <div id="DeviceType">DeviceType</div>
|名称|类型|描述|
|---|---|---|
|**deviceType**|String|实例类型, 如 edcps.c.normal1|
|**name**|String|实例类型名称, 如 边缘标准计算型Ⅰ|
|**family**|String|实例所属规格系列，如 计算、存储、GPU|
|**region**|String|区域代码, 如 cn-east-tz1|
|**cpuConcise**|String|CPU概要描述|
|**cpuDetail**|String|CPU详细信息|
|**memConcise**|String|内存概要信息|
|**memDetail**|String|内存详细信息|
|**ifConcise**|String|网口概要信息|
|**ifDetail**|String|网口详细信息|
|**gpuConcise**|String|GPU概要信息|
|**gpuDetail**|String|GPU详细信息|
|**systemDiskAmount**|Integer|系统盘数量|
|**systemDiskSize**|Integer|系统盘单盘大小（GB）|
|**systemDiskModel**|String|系统盘规格|
|**dataDiskAmount**|Integer|数据盘数量|
|**dataDiskSize**|Integer|数据盘单盘大小（GB）|
|**dataDiskModel**|String|数据盘规格|
|**isSoldOut**|Boolean|售罄状态|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
