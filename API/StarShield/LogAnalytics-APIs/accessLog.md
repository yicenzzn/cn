# accessLog


## 描述
访问日志.

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$accessLog

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
|**pageNumber**|Integer|False| | |
|**pageSize**|Integer|False| | |
|**filters**|[AnalyticsReportingFilter[]](accessLog#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](accessLog#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**total**|Number| |
|**dataList**|[AccessLog[]](accessLog#accesslog)| |
### <div id="accesslog">AccessLog</div>
|名称|类型|描述|
|---|---|---|
|**timestamp**|String| |
|**ip**|String| |
|**country**|String| |
|**httpMethod**|String| |
|**host**|String| |
|**requestUri**|String| |
|**httpProtocol**|String| |
|**responseStatus**|Integer| |
|**responseBytes**|Integer| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
