# queryBillDetail


## 描述
查询账单明细数据

## 请求方式
POST

## 请求地址
https://billing.jdcloud-api.com/v1/regions/{regionId}/billDetail:list

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**startTime**|String|True| |帐单开始时间|
|**endTime**|String|True| |帐单结束时间|
|**appCode**|String|False| |产品线代码|
|**serviceCode**|String|False| |产品代码|
|**billingType**|Integer|False| |计费类型 1、按配置 2、按用量 3、包年包月 4、按次|
|**resourceIds**|String[]|False| |资源单id列表,最多支持传入500个|
|**tags**|Map[]|False| |标签|
|**pageIndex**|Integer|True| |pageIndex 分页 从1开始,java客户端调用默认值1，其它客户端必传|
|**pageSize**|Integer|True| |pageSize 每页查询数据条数，最多支持200条,java客户端调用默认值10，其它客户端必传|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**pagination**|Pagination| |
|**result**|BillSummary[]| |
### BillSummary
|名称|类型|描述|
|---|---|---|
|**pin**|String|用户pin|
|**appCode**|String|appCode|
|**appCodeName**|String|产品线代码名称|
|**serviceCode**|String|serviceCode|
|**serviceCodeName**|String|产品代码名称|
|**billingType**|Integer|计费类型|
|**billingTypeName**|String|计费类型描述|
|**resourceId**|String|资源id|
|**resourceName**|String|资源名称|
|**region**|String|区域|
|**actionTypeName**|String|费用类型|
|**formula**|String|规格|
|**startTime**|String|计费开始时间|
|**endTime**|String|计费结束时间|
|**billTime**|String|账单生成时间|
|**totalFee**|Number|账单总额|
|**discountFee**|Number|优惠金额|
|**realTotalFee**|Number|优惠后总价金额|
|**cashCouponPayFee**|Number|代金券支付金额|
|**balancePayFee**|Number|余额支付金额|
|**cashPayFee**|Number|现金支付金额|
|**arrearFee**|Number|欠费金额|
|**tagDetails**|ResourceTagVo[]|标签明细|
### ResourceTagVo
|名称|类型|描述|
|---|---|---|
|**tagKey**|String|标签键|
|**tagValue**|String|标签值|
### Pagination
|名称|类型|描述|
|---|---|---|
|**currPageNo**|Integer|当前页|
|**numberPages**|Integer|总页数|
|**numberRecords**|Integer|总记录数|
|**pageSize**|Integer|每页记录数,默认10|
|**startIndex**|Integer|起始页|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|

## 请求示例

POST

```
调用方法、签名算法及公共请求参数请参考[京东云OpenAPI公共说明](https://docs.jdcloud.com/common-declaration/api/introduction)。
- 请求示例: 查询2021-1-31日资源vol-2iflk2kc95的账单明细数据
{
  "regionId": "cn-north-1",
  "serviceCode":"disk",
  "resourceIds": ["vol-2iflt2kc95"],
  "startTime": "2021-01-31 00:00:00",
  "endTime": "2021-01-31 23:59:59",
  "pageIndex": 1,
  "pageSize": 10
}
```

## 返回示例

```
{
    "result": {
        "pagination": {
            "currPageNo": 1, 
            "numberPages": 3, 
            "numberRecords": 24, 
            "pageSize": 10, 
            "startIndex": 0
        }, 
        "result": [
            {
                "actionTypeName": "按量费用", 
                "appCode": "jcloud", 
                "appCodeName": "基础云", 
                "arrearFee": 0.0, 
                "balancePayFee": 0.0, 
                "billTime": "2021-01-31 00:16:58", 
                "billingType": 1, 
                "billingTypeName": "按配置", 
                "cashCouponPayFee": 0.03, 
                "cashPayFee": 0.0, 
                "discountFee": 0.0, 
                "endTime": "2021-01-30 23:59:59", 
                "formula": "通用型ssd:40GB", 
                "pin": "jcloudiaas5", 
                "realTotalFee": 0.03, 
                "region": "cn-north-1", 
                "resourceId": "vol-2iflt2kc95", 
                "resourceName": "", 
                "serviceCode": "disk", 
                "serviceCodeName": "云硬盘", 
                "startTime": "2021-01-30 23:00:00", 
                "tagDetails": [
                    {
                        "tagKey": "部门", 
                        "tagValue": "商业平台部"
                    }
                ], 
                "totalFee": 0.03
            }, 
            {
                "actionTypeName": "按量费用", 
                "appCode": "jcloud", 
                "appCodeName": "基础云", 
                "arrearFee": 0.0, 
                "balancePayFee": 0.0, 
                "billTime": "2021-01-31 01:16:56", 
                "billingType": 1, 
                "billingTypeName": "按配置", 
                "cashCouponPayFee": 0.03, 
                "cashPayFee": 0.0, 
                "discountFee": 0.0, 
                "endTime": "2021-01-31 00:59:59", 
                "formula": "通用型ssd:40GB", 
                "pin": "jcloudiaas5", 
                "realTotalFee": 0.03, 
                "region": "cn-north-1", 
                "resourceId": "vol-2iflt2kc95", 
                "resourceName": "", 
                "serviceCode": "disk", 
                "serviceCodeName": "云硬盘", 
                "startTime": "2021-01-31 00:00:00", 
                "tagDetails": [
                    {
                        "tagKey": "部门", 
                        "tagValue": "商业平台部"
                    }
                ], 
                "totalFee": 0.03
            }, 
            {
                "actionTypeName": "按量费用", 
                "appCode": "jcloud", 
                "appCodeName": "基础云", 
                "arrearFee": 0.0, 
                "balancePayFee": 0.0, 
                "billTime": "2021-01-31 02:16:57", 
                "billingType": 1, 
                "billingTypeName": "按配置", 
                "cashCouponPayFee": 0.03, 
                "cashPayFee": 0.0, 
                "discountFee": 0.0, 
                "endTime": "2021-01-31 01:59:59", 
                "formula": "通用型ssd:40GB", 
                "pin": "jcloudiaas5", 
                "realTotalFee": 0.03, 
                "region": "cn-north-1", 
                "resourceId": "vol-2iflt2kc95", 
                "resourceName": "", 
                "serviceCode": "disk", 
                "serviceCodeName": "云硬盘", 
                "startTime": "2021-01-31 01:00:00", 
                "tagDetails": [
                    {
                        "tagKey": "部门", 
                        "tagValue": "商业平台部"
                    }
                ], 
                "totalFee": 0.03
            }
        ]
    }
}
```