# describeUsage


## 描述
查询配额使用量，支持查询合作云产品所有的配额。


## 请求方式
GET

## 请求地址
https://cocquota.jdcloud-api.com/v1/regions/{regionId}/quota:describeUsage

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID。|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ownerType**|String|False| |配额所属类型。<br>1.当此参数为空，默认查询用户对应合作云产品的配额使用量。<br>  示例如下：<br>  比如想查询合作云主机的配额使用情况，则此参数不用传<br>2.当需要查询某个资源的关联资源配额时，参数值为：resource_id。<br>  示例如下：<br>  比如想查询某个路由表下路由的配额情况，那么`ownerType`传参`resource_id`，`ownerId`传参具体的路由表ID，`serviceCode`传`cocvpc`,`resourceType`传`route`<br>|
|**ownerId**|String|False| |配额所属ID。只有`ownerType`传参为`resource_id`的时候，需要传此参数。|
|**serviceCode**|String|False| |服务标识。<br>当 ownerType 为 resource_id，此参数必传。<br>当 ownerType 为 空或者其他值，此参数如果为空，则查询当前用户的所有配额使用量列表。<br>支持的参数为: `cocvm`, `cocdisk`, `cocvpc`, `cocip`<br>|
|**resourceType**|String|False| |资源类型。<br>当 ownerType 为 resource_id，此参数必传。<br>当 ownerType 为 空或者其他值，此参数如果为空，则查询当前用户的所有配额使用量列表。<br>当 `serviceCode` 为 `cocvm`, 此参数可选值：`vm`, `image`, `keypair`<br>当 `serviceCode` 为 `cocdisk`, 此参数可选值：`volume`, `volume_size`, `snapshot`<br>当 `serviceCode` 为 `cocvpc`, 此参数可选值：`vpc`, `subnet`, `acl`, `aclRule`, `routeTable`, `route`, `securityGroup`, `securityGroupRule`<br>当 `serviceCode` 为 `cocip`, 此参数可选值：`elasticIp`<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|响应结果。|
|**requestId**|String|请求ID。|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**quotaUsages**|[QuotaUsage[]](#quotausage)|配额使用量列表。|
### <div id="QuotaUsage">QuotaUsage</div>
|名称|类型|描述|
|---|---|---|
|**pin**|String|用户pin。|
|**region**|String|地域。|
|**ownerId**|String|配额的拥有者ID。|
|**ownerType**|String|配额的拥有者类型。可选值：resource_id。<br>如果为空或者其他值，则配额拥有者类型则默认为用户。<br>|
|**quotaId**|String|配额类型ID。|
|**serviceCode**|String|服务标识。|
|**resourceType**|String|资源类型。|
|**limit**|Integer|配额上限。|
|**used**|Integer|已用配额。|
|**createTime**|String|配额使用量的创建时间。|
|**updateTime**|String|配额使用量的更新时间。|

## 返回码
|HTTP状态码|错误码|描述|错误解析|
|---|---|---|---|
|**200**||OK||
|**500**|INTERNAL|Internal server error|系统内部错误，请稍后重试。如果多次尝试失败，请提交工单。|
|**500**|UNKNOWN|Unknown server error|服务暂时不可用，请稍后重试。如果多次尝试失败，请提交工单。|

## 请求示例
GET
```

### 场景1：查询当前用户的虚机的配额使用情况

- 请求
/v1/regions/cn-hongkong-11/quota:describeUsage?serviceCode=cocvm&resourceType=vm

- 返回
{
  "requestId": "request-id-for-test-coc-3",
  "result": {
    "quotaUsages": [
      {
        "region": "cn-hongkong-11",
        "pin": "abc",
        "ownerId": "abc",
        "ownerType": "pin",
        "quotaId": "quota-222eee",
        "serviceCode": "cocvm",
        "resourceType": "vm",
        "limit": 100,
        "used": 27,
        "createTime": "2022-08-03 14:49:17",
        "updateTime": "2022-09-30 16:40:32"
      }
    ]
  }
}

### 场景2：查询某个路由表的创建路由的配额情况,那么`ownerType`传参`resource_id`，`ownerId`传参具体的路由表ID，`serviceCode`传`cocvpc`,`resourceType`传`route`

- 请求
/v1/regions/cn-hongkong-11/quota:describeUsage?ownerType=resource_id&ownerId=rtb-abc123&serviceCode=cocvpc&resourceType=route

- 返回
{
  "requestId": "request-id-for-test-coc-3",
  "result": {
    "quotaUsages": [
      {
        "region": "cn-hongkong-11",
        "pin": "abc",
        "ownerId": "rtb-abc123",
        "ownerType": "resource_id",
        "quotaId": "quota-123aaa",
        "serviceCode": "cocvpc",
        "resourceType": "route",
        "limit": 50,
        "used": 3,
        "createTime": "2022-10-31 19:30:02",
        "updateTime": "2022-10-31 19:30:02"
      }
    ]
  }
}

```
