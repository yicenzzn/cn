# editRule


## 描述
更新规则在域上触发时将执行的操作

## 请求方式
PATCH

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_id}/firewall$$waf$$packages/{package_id}/rules/{identifier}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_id**|String|True| | |
|**package_id**|String|True| | |
|**identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**mode**|String|False| |触发规则时使用的模式。值基于规则的allowed_modes进行限制。有效值default/disable/simulate/block/challenge/on/off|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](editRule#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[WAFRule](editRule#wafrule)| |
### <div id="wafrule">WAFRule</div>
|名称|类型|描述|
|---|---|---|
|**id**|String|WAF规则标识符标签|
|**description**|String|规则的公开说明|
|**priority**|String|在相关组中执行单个规则的顺序|
|**group**|[Group](editRule#group)| |
|**package_id**|String|WAF包标识符标签|
|**allowed_modes**|String[]|定义触发规则时规则交互方式的可用模式。|
|**default_mode**|String|规则的默认模式。|
|**mode**|String|评估请求时是否使用基于异常的规则。|
### <div id="group">Group</div>
|名称|类型|描述|
|---|---|---|
|**id**|String|WAF组标识符标签|
|**name**|String|防火墙规则组的名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
