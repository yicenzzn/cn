# bandwidthTopK


## 描述
按响应带宽统计。获取国家/地区的请求分布情况；获取路径、主机、设备类型的TopK.

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$bandwidthTopK

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zoneName**|String|False| | |
|**since**|String|False| | |
|**until**|String|False| | |
|**topK**|Integer|False| | |
|**filters**|[AnalyticsReportingFilter[]](bandwidthTopK#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](bandwidthTopK#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**topkAnalytics**|[TopkAnalytics](bandwidthTopK#topkanalytics)| |
### <div id="topkanalytics">TopkAnalytics</div>
|名称|类型|描述|
|---|---|---|
|**countries**|[Item[]](bandwidthTopK#item)| |
|**topCountries**|[Item[]](bandwidthTopK#item)| |
|**topDeviceTypes**|[Item[]](bandwidthTopK#item)| |
|**topHosts**|[Item[]](bandwidthTopK#item)| |
|**topPaths**|[Item[]](bandwidthTopK#item)| |
|**topContentTypes**|[Item[]](bandwidthTopK#item)| |
|**topStatusCodes**|[Item[]](bandwidthTopK#item)| |
|**topIPs**|[Item[]](bandwidthTopK#item)| |
|**topUserAgents**|[Item[]](bandwidthTopK#item)| |
|**topHttpMethods**|[Item[]](bandwidthTopK#item)| |
|**topASNs**|[Item[]](bandwidthTopK#item)| |
|**topFirewallRuleIds**|[Item[]](bandwidthTopK#item)| |
|**topFirewallRules**|[Item[]](bandwidthTopK#item)| |
|**topWafRuleIds**|[Item[]](bandwidthTopK#item)| |
|**topWafRules**|[Item[]](bandwidthTopK#item)| |
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
