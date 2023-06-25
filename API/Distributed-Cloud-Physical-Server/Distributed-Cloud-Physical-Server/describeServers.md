# describeServers


## 描述
查询后端服务器列表

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/serverGroups/{serverGroupId}/servers

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeCPSLBRegions）获取云物理服务器支持的地域|
|**serverGroupId**|String|True| |服务器组ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False|1|页码；默认为1|
|**pageSize**|Integer|False|20|分页大小；默认为20；取值范围[20, 100]|
|**listenerId**|String|False| |监听器Id|
|**filters**|[Filter[]](#filter)|False| |serverId - 后端服务器ID，精确匹配，支持多个<br>|

### <div id="Filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**servers**|[Server[]](#server)| |
|**pageNumber**|Integer|页码；默认为1|
|**pageSize**|Integer|分页大小；默认为20；取值范围[20, 100]|
|**totalCount**|Integer|查询结果总数|
### <div id="Server">Server</div>
|名称|类型|描述|
|---|---|---|
|**serverId**|String|服务器ID|
|**instanceType**|String|资源类型|
|**instanceName**|String|实例名称|
|**instanceId**|String|后端云物理服务器ID|
|**az**|String|可用区|
|**privateIp**|String|内网Ip|
|**port**|Integer|端口|
|**weight**|Integer|后端云物理服务器权重|
|**status**|String|状态|
|**healthyStatus**|String|健康状态|
|**aliasip**|String|别名IP|
|**iptype**|String|IP类型：别名IPv4 or 内网IPv4|
|**rip**|String|别名IPv4 或 内网IPv4 的真实值|
|**nicMode**|String|bond：单网卡模式；normal：双网卡模式|
|**interfaceName**|String|bond0 单网口-主网口； eth0 双网口-主网口 ；eth1 双网口-辅网口|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
