# getDomainList


## 描述
查询加速域名接口

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**keyWord**|String|False| |根据关键字进行模糊匹配|
|**pageNumber**|Integer|False|1|pageNumber,默认值1|
|**pageSize**|Integer|False|20|pageSize,最大值50,默认值20|
|**status**|String|False| |根据域名状态查询, 可选值[offline, online, configuring, auditing, audit_reject]|
|**type**|String|False| |域名类型，(web:静态小文件，download:大文件加速，vod:视频加速，live:直播加速),不传查所有|
|**accelerateRegion**|String|False| |加速区域，(mainland:中国大陆，nonMainland:海外加港澳台，all:全球),不传查所有|
|**withThirdPartyStatus**|Boolean|False| |筛选依据，查询域名海外状态（false不需要查询, true 需要查询海外状态)默认false|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getdomainlist#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**totalCount**|Integer| |
|**pageSize**|Integer| |
|**pageNumber**|Integer| |
|**domains**|[ListDomainItem[]](getdomainlist#listdomainitem)|域名列表|
### <div id="listdomainitem">ListDomainItem</div>
|名称|类型|描述|
|---|---|---|
|**cname**|String| |
|**description**|String| |
|**domain**|String| |
|**created**|String| |
|**modified**|String| |
|**status**|String|加速域名中国境内运行状态 ，online 表示启用；offline表示停用；configuring表示配置中；configure_failed表示配置失败 |
|**wafStatus**|String| |
|**type**|String| |
|**auditStatus**|String| |
|**accelerateRegion**|String| |
|**overseaStatus**|Long|加速域名海外运行状态(-1:不涉及海外加速,0:未激活,1:已激活,2:海外无该域名)；当withThirdPartyStatus为false时，overseaStatus默认为-1|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
