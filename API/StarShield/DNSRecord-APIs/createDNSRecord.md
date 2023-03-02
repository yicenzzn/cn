# createDNSRecord


## 描述
创建DNS记录

## 请求方式
POST

## 请求地址
https://starshield.jdcloud-api.com/v1/zones/{zone_identifier}/dns_records

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**zone_identifier**|String|True| | |

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ty_pe**|String|False| |DNS记录类型|
|**name**|String|True| |DNS记录名称|
|**content**|String|True| |DNS记录内容|
|**ttl**|Number|True| |DNS记录的生存时间。值为1是 "自动"。|
|**priority**|Number|False| |与一些记录如MX和SRV一起使用，以确定优先级。如果你没有为MX记录提供一个优先级，默认值为0将被设置。|
|**proxied**|Boolean|False| |是否利用星盾的性能和安全优势|
|**srvData**|[SRVdata](createDNSRecord#srvdata)|False| | |
|**caaData**|[CAAdata](createDNSRecord#caadata)|False| | |

### <div id="caadata">CAAdata</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**flags**|Number|False| | |
|**tag**|String|False| | |
|**value**|String|False| | |
### <div id="srvdata">SRVdata</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**priority**|Number|False| | |
|**weight**|Number|False| | |
|**port**|Number|False| | |
|**name**|String|False| | |
|**proto**|String|False| | |
|**service**|String|False| | |
|**target**|String|False| | |

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createDNSRecord#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DnsRecord](createDNSRecord#dnsrecord)| |
### <div id="dnsrecord">DnsRecord</div>
|名称|类型|描述|
|---|---|---|
|**meta**|[Meta](createDNSRecord#meta)| |
|**locked**|Boolean|此记录是否可以被修改/删除（true意味着它由星盾管理）。|
|**data**|[Data](createDNSRecord#data)| |
|**name**|String|DNS记录名称|
|**ttl**|Number|DNS记录的生存时间。值为1是 "自动"。|
|**zone_id**|String|域标识符标签|
|**modified_on**|String|记录最近修改时间|
|**created_on**|String|创建记录时间|
|**proxiable**|Boolean|记录是否由星盾代理|
|**content**|String|有效的IPv4地址|
|**type**|String|记录类型|
|**ty_pe**|String|记录类型(值同type)|
|**id**|String|DNS记录标识符标签|
|**proxied**|Boolean|是否利用星盾的性能和安全优势|
|**zone_name**|String|记录的域名|
|**priority**|Number|与一些记录如MX和SRV一起使用，以确定优先级。如果你没有为MX记录提供一个优先级，默认值为0将被设置。|
### <div id="data">Data</div>
|名称|类型|描述|
|---|---|---|
|**size**|Number|位置的大小（米）|
|**altitude**|Number|位置高度（米）|
|**long_degrees**|Number|经度|
|**lat_degrees**|Number|纬度|
|**precision_horz**|Number|水平定位精度|
|**precision_vert**|Number|垂直定位精度|
|**long_direction**|String|经度方向|
|**long_minutes**|Number|经度分|
|**long_seconds**|Number|经度秒|
|**lat_direction**|String|纬度方向|
|**lat_minutes**|Number|纬度分|
|**lat_seconds**|Number|纬度秒|
|**service**|String|以下划线为前缀的服务类型|
|**proto**|String|有效的协议|
|**name**|String|有效的主机名|
|**priority**|Number|与一些记录如MX和SRV一起使用，以确定优先级。如果你没有为MX记录提供一个优先级，默认值为0将被设置。|
|**weight**|Number|记录的权重|
|**port**|Number|服务的端口|
|**target**|String|有效的主机名|
|**ty_pe**|Number|类型|
|**key_tag**|Number|Key Tag|
|**algorithm**|Number|Algorithm|
|**certificate**|String|证书|
|**flags**|Number|Flags|
|**protocol**|Number|协议|
|**public_key**|String|公钥|
|**digest_type**|Number|摘要类型|
|**digest**|String|摘要|
|**order**|Number|Order|
|**preference**|Number|Preference|
|**regex**|String|Regex|
|**replacement**|String|Replacement|
|**usage**|Number|Usage|
|**selector**|Number|Selector|
|**matching_type**|Number|Matching Type|
|**fingerprint**|String|指纹|
|**content**|String|记录内容|
### <div id="meta">Meta</div>
|名称|类型|描述|
|---|---|---|
|**auto_added**|Boolean|如果星盾在初始设置期间自动添加了此 DNS 记录，则会存在。|
|**source**|String|记录来自哪里|

## 返回码
|返回码|描述|
|---|---|
|**200**|request successful|
