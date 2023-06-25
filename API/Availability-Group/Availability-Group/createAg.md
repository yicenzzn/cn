# createAg


## 描述
创建一个高可用组，高可用组支持如下三个置放维度：
* 物理机维度：高可用组内所有实例严格分散在指定地域的不同物理机上，单可用区内实例数量上限为10；
* 交换机维度：高可用组内所有实例严格分散在指定地域的不同交换机下，单可用区内实例数量上限为5；
* 故障域维度（默认）：高可用组内实例分散部署在相互隔离的物理资源（故障域）上，每个高可用组会自动划分为5个故障域，多台实例可以根据实际需要分散部署在不同的分组当中，相同分组的实例不保障严格分散部署。

## 请求方式
POST

## 请求地址
https://ag.jdcloud-api.com/v1/regions/{regionId}/availabilityGroups

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**azs**|String[]|True| |支持的可用区，最少一个|
|**agName**|String|True| |高可用组名称，只支持中文、数字、大小写字母、英文下划线 “_” 及中划线 “-”，且不能超过 32 字符|
|**agType**|String|False| |高可用组类型，支持vm|
|**instanceTemplateId**|String|False| |实例模板的Id，创建strict类型的高可用组时此项为必填项|
|**placement**|string|False| |高可用组中资源的放置类型。可选值：<br> `fd`(默认值）：故障域维度打散 <br> `host`：物理机维度打散 <br> `switch`：交换机维度打散
|**description**|String|False| |描述，长度不超过 256 字符|
|**configurationType**|String|False| |高可用组配置类型。 可选值：<br> `strict`(默认值）：关联模板型 <br> `loose`：自定义配置型|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**agId**|String|创建成功的高可用组 id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
