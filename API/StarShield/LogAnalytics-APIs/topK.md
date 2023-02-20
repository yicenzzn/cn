# topK


## 描述
按请求次数统计。获取国家/地区的请求分布情况；获取路径、主机、设备类型的TopK.

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$topK

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
|**filters**|[AnalyticsReportingFilter[]](topK#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](topK#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**topkAnalytics**|[TopkAnalytics](topK#topkanalytics)| |
### <div id="topkanalytics">TopkAnalytics</div>
|名称|类型|描述|
|---|---|---|
|**countries**|[Item[]](topK#item)| |
|**topCountries**|[Item[]](topK#item)| |
|**topDeviceTypes**|[Item[]](topK#item)| |
|**topHosts**|[Item[]](topK#item)| |
|**topPaths**|[Item[]](topK#item)| |
|**topContentTypes**|[Item[]](topK#item)| |
|**topStatusCodes**|[Item[]](topK#item)| |
|**topIPs**|[Item[]](topK#item)| |
|**topUserAgents**|[Item[]](topK#item)| |
|**topHttpMethods**|[Item[]](topK#item)| |
|**topASNs**|[Item[]](topK#item)| |
|**topFirewallRuleIds**|[Item[]](topK#item)| |
|**topFirewallRules**|[Item[]](topK#item)| |
|**topWafRuleIds**|[Item[]](topK#item)| |
|**topWafRules**|[Item[]](topK#item)| |
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
