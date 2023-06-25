# describeDiskSpecification


## 描述
-   提供云硬盘支持规格的详情


## 请求方式
GET

## 请求地址
https://coc.disk.jdcloud-api.com/v1/regions/{regionId}/disks:diskSpecification

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**az**|String|False| |查询所指定az的云硬盘规格|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|查询结果集|
|**requestId**|String|请求ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**diskSpecification**|[DiskSpecification[]](describeDiskSpecification#DiskSpecification)|查询的云硬盘规格信息详情列表|
|**totalCount**|Integer|查询的云硬盘规格数目|
### <div id="DiskSpecification">DiskSpecification</div>
|名称|类型|描述|
|---|---|---|
|**diskType**|String|云硬盘类型|
|**minSizeGB**|Integer|支持的最小尺寸，单位为 GiB|
|**maxSizeGB**|Integer|支持的最大尺寸，单位为 GiB|
|**stepSizeGB**|Integer|步长尺寸，单位为 GiB|
|**description**|String|描述信息|
|**diskTypeName**|String|类型名称|
|**defaultIOPS**|Integer|默认的iops数量(基础iops数量)|
|**stepIOPS**|Float|iops步长增量|
|**maxIOPS**|Integer|最大iops数量|
|**defaultThroughput**|Integer|默认的吞吐量|
|**stepThroughput**|Float|吞吐量步长增量|
|**maxThroughput**|Integer|最大吞吐量|
|**scalableIOPS**|Boolean|是否开启IOPS可调整|
|**maxStepIOPS**|Integer|最大iops步长|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
