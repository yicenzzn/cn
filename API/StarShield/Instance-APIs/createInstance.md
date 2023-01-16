# createInstance


## 描述
创建套餐实例，调用成功，将自动扣费（请保证账户充足，否则无法成功创建实例）。


## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**x-jdcloud-source**|String|True| |请求头x-jdcloud-source必须赋值为sdk<br>|
|**chargeMode**|String|True| |计费模式（CONFIG、FLOW、MONTHLY、ONCE）<br>CONFIG 按配置<br>FLOW 按用量<br>MONTHLY 包年包月<br>ONCE 一次性<br>|
|**packType**|String|True| |套餐类型（BASIC、PROFESSIONAL、ENTERPRISE、ULTIMATE、SMB_EXPERIENCE、SMB_BASIC、SMB_BUSINESS）<br>BASIC 包年包月 基础版<br>PROFESSIONAL 包年包月 专业版<br>ENTERPRISE 包年包月 企业版<br>ULTIMATE 包年包月 旗舰版<br>--------------------------<br>SMB_EXPERIENCE 按流量 体验版<br>SMB_BASIC 按流量 基础版<br>SMB_BUSINESS 按流量 商业版<br>|
|**zonePackNum**|Integer|False| |域名增量包数量|
|**duration**|Integer|False| |计费时长|
|**durationUnit**|String|False| |计费时长单位（MONTH、YEAR）|
|**autoRenewStatus**|String|False|CLOSE|自动续费状态(OPEN->开通自动续费 CLOSE->关闭自动续费)|
|**instanceName**|String|True| |实例名称|
|**memo**|String|False| |备注|
|**returnUrl**|String|False| |支付成功返回路径|
|**buyScenario**|String|False| |购买上下文JSON字符串|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createInstance#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**buyId**|String|购买ID，可通过调用describeInstanceByOrderNo接口获取实例详情|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
