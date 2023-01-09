## 应用安全网关日志
### 简介
目前接入日志服务的应用安全官网日志类型为WAF访问日志。

### 字段说明
日志字段 | 字段描述 | 字段类型
-- | -- | --
time | 时间 | time
waf_id | wafid | string
weblock_hit | 是否命中网页防篡改 | string
cc_hit | 是否命中cc | string
urule_hit | 是否命中用户规则 | string
waf_hit | 是否命中waf规则 | string
remote_addr | 访问源地址 | string
server_addr | 服务器地址 | string
request_method | 请求方法 | string
host | host | string
request_uri | 请求uri | string