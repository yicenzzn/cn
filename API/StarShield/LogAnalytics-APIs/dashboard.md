# dashboard


## 描述
The dashboard view provides both totals and timeseries data for the given zone and time period across the entire scdn network.

## 请求方式
GET

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$dashboard

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zoneName**|String|True| | |
|**since**|String|True| | |
|**until**|String|True| | |
|**category**|String|False| | |
|**filters**|[AnalyticsReportingFilter[]](dashboard#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](dashboard#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**zoneAnalytics**|[ZoneAnalytics](dashboard#zoneanalytics)| |
### <div id="zoneanalytics">ZoneAnalytics</div>
|名称|类型|描述|
|---|---|---|
|**totals**|[Totals](dashboard#totals)| |
|**timeseries**|[Totals[]](dashboard#totals)|Time deltas containing metadata about each bucket of time. The number of buckets (resolution) is determined by the amount of time between the since and until parameters.|
### <div id="totals">Totals</div>
|名称|类型|描述|
|---|---|---|
|**since**|String| |
|**until**|String| |
|**requests**|[Requests](dashboard#requests)| |
|**bandwidth**|[Bandwidth](dashboard#bandwidth)| |
### <div id="bandwidth">Bandwidth</div>
|名称|类型|描述|
|---|---|---|
|**all**|Number|The total number of bytes served within the time frame|
|**all_beautified**|String| |
|**cached**|Number|The number of bytes that were cached (and served) by scdn|
|**cached_beautified**|String| |
|**cachedPercentage**|String| |
### <div id="requests">Requests</div>
|名称|类型|描述|
|---|---|---|
|**all**|Number|Total number of requests served|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
