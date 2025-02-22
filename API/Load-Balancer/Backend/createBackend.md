# createBackend


## 描述
创建一个后端服务

## 请求方式
POST

## 请求地址
https://lb.jdcloud-api.com/v1/regions/{regionId}/backends/

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**backendName**|String|True| |后端服务名字,只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符|
|**loadBalancerId**|String|True| |后端服务所属负载均衡的Id|
|**protocol**|String|True| |后端服务的协议 <br>【alb】取值范围：Http、Tcp、Udp <br>【nlb】取值范围：Tcp、Udp <br>【dnlb】取值范围：Tcp、Udp|
|**port**|Integer|True| |后端服务的端口，取值范围为[1, 65535]，如指定了TargetSpec中的port，实际按照target指定的port进行转发|
|**healthCheckSpec**|[HealthCheckSpec](createbackend#healthcheckspec)|True| |健康检查信息|
|**algorithm**|String|False| |调度算法 <br>【alb,nlb】取值范围为[IpHash, RoundRobin, LeastConn]（取值范围的含义：加权源Ip哈希，加权轮询和加权最小连接），alb和nlb默认为加权轮询 <br>【dnlb】取值范围为[IpHash, QuintupleHash]（取值范围的含义分别为：加权源Ip哈希和加权五元组哈希），dnlb默认为加权源Ip哈希|
|**targetGroupIds**|String[]|False| |虚拟服务器组的Id列表，目前只支持一个，且与agIds不能同时存在|
|**agIds**|String[]|False| |高可用组的Id列表，目前只支持一个，且与targetGroupIds不能同时存在|
|**proxyProtocol**|Boolean|False| |【alb Tcp、Udp协议】获取真实ip, 取值为False(不获取)或者True(获取,支持Proxy Protocol v1版本)，默认为False|
|**description**|String|False| |描述,允许输入UTF-8编码下的全部字符，不超过256字符|
|**sessionStickiness**|Boolean|False| |会话保持, 取值为false(不开启)或者true(开启)，默认为false <br>【alb Http协议，RoundRobin算法】支持基于cookie的会话保持 <br>【nlb】支持基于报文源目的IP的会话保持|
|**sessionStickyTimeout**|Integer|False| |【nlb】会话保持超时时间，sessionStickiness开启时生效，默认300s, 取值范围[1-3600]|
|**connectionDrainingSeconds**|Integer|False| |【nlb】连接耗尽超时。移除target前，连接的最大保持时间，默认300s，取值范围[0-3600]|
|**httpCookieExpireSeconds**|Integer|False| |【alb Http协议】cookie的过期时间,sessionStickiness开启时生效，取值范围为[0-86400], 默认为0（表示cookie与浏览器同生命周期）|
|**httpForwardedProtocol**|Boolean|False| |【alb Http协议】获取负载均衡的协议, 取值为False(不获取)或True(获取), 默认为False|
|**httpForwardedPort**|Boolean|False| |【alb Http协议】获取负载均衡的端口, 取值为False(不获取)或True(获取), 默认为False|
|**httpForwardedHost**|Boolean|False| |【alb Http协议】获取负载均衡的host信息, 取值为False(不获取)或True(获取), 默认为False|
|**httpForwardedVip**|Boolean|False| |【alb Http协议】获取负载均衡的vip, 取值为False(不获取)或True(获取), 默认为False|
|**httpForwardedClientPort**|Boolean|False| |【alb Http协议】获取请求端使用的端口, 取值为False(不获取)或True(获取), 默认为False|

### <div id="healthcheckspec">HealthCheckSpec</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**protocol**|String|True| |健康检查协议 <br>【alb、nlb】取值为Http, Tcp, Icmp(仅支持alb/nlb的Udp的Backend) <br>【dnlb】取值为Tcp, Icmp(仅支持dnlb的Udp的Backend)|
|**healthyThresholdCount**|Integer|False| |健康阀值，取值范围为[1,5]，默认为3|
|**unhealthyThresholdCount**|Integer|False| |不健康阀值，取值范围为[1,5], 默认为3|
|**checkTimeoutSeconds**|Integer|False| |响应超时时间, 取值范围为[2,60]，默认为3s|
|**intervalSeconds**|Integer|False| |健康检查间隔, 范围为[5,300], 默认为5s|
|**port**|Integer|False| |健康检查的目标端口, 取值范围为[0,65535], 默认为0，默认端口为每个后端实例接收负载均衡流量的端口，Icmp类型不支持配置端口|
|**httpDomain**|String|False| |健康检查的目标域名，仅支持HTTP协议。支持输入域名和IP地址。如果输入域名，仅支持大小写字母、数字、英文中划线"-"和点"."，不区分大小写，且不超过255个字符。默认为空，表示健康检查不携带域名|
|**httpPath**|String|False| |健康检查的目标路径，仅支持HTTP协议。必须以"/"开头，支持大小写字母、数字、汉字和英文字符-/.%?#&_;~!()*[]@^:',+=<>{}。%后仅支持输入URL编码后字符，且不超过1000个字符|
|**httpCode**|String[]|False| |检查来自后端目标服务器的成功响应时，要使用的HTTP状态码。您可以指定单个数值（例如："200"，取值范围200-499）、一段连续数值（例如："201-205"，取值范围范围200-499，且前面的参数小于后面）和一类连续数值缩写（例如："3xx"，等价于"300-399"，取值范围2xx、3xx和4xx）。多个数值之间通过","分割（例如："200,202-207,302,4xx"）。目前仅支持2xx、3xx、4xx。仅支持HTTP协议，默认为[2xx、3xx]|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createbackend#result)|返回结果|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**backendId**|String|后端服务id|

## 返回码
|返回码|描述|
|---|---|
|**200**|Successful operation|
|**409**|backend.inuse.name:backend name 'xxx' is already exist|
|**404**|Resource not found|
|**429**|Quota limit backend exceeded.|
|**400**|Request parameter x.y.z is 'xxx', expected one of [yyy,zzz]|
