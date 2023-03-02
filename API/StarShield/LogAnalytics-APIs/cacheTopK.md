# cacheTopK


## 描述
按请求次数统计。获取内容类型、路径、主机、设备类型、国家/地区、状态代码的TopK.

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$cacheTopK

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**x-jdcloud-account-id**|String|True| |请求头：实例id|
|**zoneName**|String|False| | |
|**since**|String|False| | |
|**until**|String|False| | |
|**topK**|Integer|False| | |
|**filters**|[AnalyticsReportingFilter[]](cacheTopK#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](cacheTopK#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**countries**|[Item[]](cacheTopK#item)| |
|**topCountries**|[Item[]](cacheTopK#item)| |
|**topDeviceTypes**|[Item[]](cacheTopK#item)| |
|**topHosts**|[Item[]](cacheTopK#item)| |
|**topPaths**|[Item[]](cacheTopK#item)| |
|**topContentTypes**|[Item[]](cacheTopK#item)| |
|**topStatusCodes**|[Item[]](cacheTopK#item)| |
|**topIPs**|[Item[]](cacheTopK#item)| |
|**topUserAgents**|[Item[]](cacheTopK#item)| |
|**topHttpMethods**|[Item[]](cacheTopK#item)| |
|**topASNs**|[Item[]](cacheTopK#item)| |
|**topFirewallRuleIds**|[Item[]](cacheTopK#item)| |
|**topFirewallRules**|[Item[]](cacheTopK#item)| |
|**topWafRuleIds**|[Item[]](cacheTopK#item)| |
|**topWafRules**|[Item[]](cacheTopK#item)| |
### <div id="item">Item</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|项的名称|
|**value**|Number|项的值。<br>如果是带宽，值的单位是bps（bit per second）<br>如果是流量，值的单位是Byte<br>如果是请求量，值的单位是次数<br>|
|**unit**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
