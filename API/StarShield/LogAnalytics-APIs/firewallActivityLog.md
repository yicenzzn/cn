# firewallActivityLog


## 描述
活动日志.

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$firewallActivityLog

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zoneName**|String|False| | |
|**since**|String|False| | |
|**until**|String|False| | |
|**pageNumber**|Integer|False| | |
|**pageSize**|Integer|False| | |
|**filters**|[AnalyticsReportingFilter[]](firewallActivityLog#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](firewallActivityLog#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Number| |
|**activityLogs**|[ActivityLog[]](firewallActivityLog#activitylog)| |
### <div id="activitylog">ActivityLog</div>
|名称|类型|描述|
|---|---|---|
|**timestamp**|String| |
|**firewallAction**|String| |
|**country**|String| |
|**ip**|String| |
|**host**|String| |
|**httpMethod**|String| |
|**httpProtocol**|String| |
|**requestUri**|String| |
|**firewallSource**|String| |
|**userAgent**|String| |
|**ruleId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
