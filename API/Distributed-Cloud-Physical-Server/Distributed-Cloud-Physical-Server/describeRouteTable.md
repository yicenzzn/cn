# describeRouteTable


## 描述
查询路由表详情

## 请求方式
GET

## 请求地址
https://edcps.jdcloud-api.com/v1/regions/{regionId}/routeTables/{routeTableId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID，可调用接口（describeRegiones）获取云物理服务器支持的地域|
|**routeTableId**|String|True| |路由表ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)| |
|**requestId**|String| |

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**routeTable**|[RouteTable](#routetable)|路由表详细信息|
### <div id="RouteTable">RouteTable</div>
|名称|类型|描述|
|---|---|---|
|**routeTableId**|String|路由表ID|
|**region**|String|地域|
|**vpcId**|String|私有网络ID|
|**vpcName**|String|私有网络名称|
|**name**|String|名称|
|**createTime**|String|创建时间|
|**routes**|[Route[]](#route)|路由规则|
### <div id="Route">Route</div>
|名称|类型|描述|
|---|---|---|
|**destinationCidr**|String|目标网段|
|**nextHopType**|String|下一跳类型|
|**nextHop**|String|下一跳|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|
