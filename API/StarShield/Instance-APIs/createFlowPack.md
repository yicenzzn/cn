# createFlowPack


## 描述
购买流量包，调用成功，将自动扣费（请保证账户充足，否则无法成功创建流量包）。


## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/flowPack

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**instanceId**|String|True| |实例ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**x-jdcloud-source**|String|True| |请求头x-jdcloud-source必须赋值为sdk<br>|
|**fixedFlowPackType**|Integer|False| |定量流量包类型(1->10TB 2->50TB 3->200TB 4->1PB 5->5PB)|
|**fixedFlowPackNum**|Integer|False| |定量流量包数量|
|**flowPackNum**|Integer|False| |按需购买流量包数量|
|**returnUrl**|String|False| |支付成功返回路径|
|**buyScenario**|String|False| |购买上下文JSON字符串|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createFlowPack#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**buyId**|String|购买ID，购买ID，可通过调用describeInstanceByOrderNo接口获取流量包实例详情|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
