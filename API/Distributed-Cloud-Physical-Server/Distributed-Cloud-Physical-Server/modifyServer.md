# modifyServer


## 描述
修改后端服务器

## 请求方式
POST

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/serverGroups/{serverGroupId}/servers/{serverId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeCPSLBRegions）获取云物理服务器支持的地域|
|**serverGroupId**|String|True| |服务器组ID|
|**serverId**|String|True| |后端服务器ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**weight**|Integer|False| |权重|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**serverId**|String|后端服务器ID|
|**instanceId**|String|后端云物理服务器ID|
|**privateIp**|String|内网Ip|
|**port**|Integer|端口|
|**weight**|Integer|后端云物理服务器权重|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
