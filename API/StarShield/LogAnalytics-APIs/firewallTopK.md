# firewallTopK


## 描述
按防火墙事件数量统计。获取IP地址、用户代理、路径、主机、国家/地区、HTTP方法的TopK。

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$firewallTopK

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
|**filters**|[AnalyticsReportingFilter[]](firewallTopK#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](firewallTopK#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**topkAnalytics**|[TopkAnalytics](firewallTopK#topkanalytics)| |
### <div id="topkanalytics">TopkAnalytics</div>
|名称|类型|描述|
|---|---|---|
|**countries**|[Item[]](firewallTopK#item)| |
|**topCountries**|[Item[]](firewallTopK#item)| |
|**topDeviceTypes**|[Item[]](firewallTopK#item)| |
|**topHosts**|[Item[]](firewallTopK#item)| |
|**topPaths**|[Item[]](firewallTopK#item)| |
|**topContentTypes**|[Item[]](firewallTopK#item)| |
|**topStatusCodes**|[Item[]](firewallTopK#item)| |
|**topIPs**|[Item[]](firewallTopK#item)| |
|**topUserAgents**|[Item[]](firewallTopK#item)| |
|**topHttpMethods**|[Item[]](firewallTopK#item)| |
|**topASNs**|[Item[]](firewallTopK#item)| |
|**topFirewallRuleIds**|[Item[]](firewallTopK#item)| |
|**topFirewallRules**|[Item[]](firewallTopK#item)| |
|**topWafRuleIds**|[Item[]](firewallTopK#item)| |
|**topWafRules**|[Item[]](firewallTopK#item)| |
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
