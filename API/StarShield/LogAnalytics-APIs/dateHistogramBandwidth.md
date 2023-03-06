# dateHistogramBandwidth


## 描述
按响应带宽统计，返回日期直方图.

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/analytics$$dateHistogramBandwidth

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
|**criterionName**|String|False| | |
|**filters**|[AnalyticsReportingFilter[]](dateHistogramBandwidth#analyticsreportingfilter)|False| | |

### <div id="analyticsreportingfilter">AnalyticsReportingFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |过滤条件的名称。有效值：<br>HttpHost/URI/ResponseStatusCode/ClientDeviceType/<br>ServedBy/CacheStatus/ClientHttpMethod/ResponseContentType/<br>ASN/IP/ClientHttpProtocol/FirewallSource/UserAgent<br>|
|**operator**|String|False| |过滤条件的操作符|
|**values**|String[]|False| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](dateHistogramBandwidth#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**dateHistograms**|[DateHistogram[]](dateHistogramBandwidth#datehistogram)| |
|**timeScope**|Number[]| |
|**since**|String| |
|**util**|String| |
### <div id="datehistogram">DateHistogram</div>
|名称|类型|描述|
|---|---|---|
|**name**|String|项的名称|
|**timeseries**|Number[]|数据点集合。<br>如果是带宽，数据点的单位是bps（bit per second）<br>如果是流量，数据点的单位是Byte<br>如果是请求量，数据点的单位是次数<br>|
|**unit**|String| |
|**total**|Number|如果是带宽，它的单位是bps（bit per second），代表数据点中的最大值。<br>如果是流量，它的单位是Byte，代表数据点流量之和。<br>如果是请求量，它的单位是次数，代表数据点请求量之和。<br>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
