# getDomainDetail


## 描述
查询加速域名详情

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/domain/{domain}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](getdomaindetail#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**allStatus**|String| |
|**allowNoReferHeader**|String|是否允许空refer访问|
|**allowNullReferHeader**|String| |
|**dailyBandWidth**|Integer|日带宽（单位Mbps）|
|**forbiddenType**|String|封禁类型，取值：domain,url |
|**maxFileSize**|Long|最大单个文件大小（单位MB） |
|**minFileSize**|Long|最小单个文件大小（单位MB） |
|**sumFileSize**|Long|总文件大小（单位MB） |
|**avgFileSize**|Long|平均文件大小（单位MB） |
|**referList**|String[]|逗号隔开的域名列表 |
|**referType**|String|refer类型，取值：block（黑名单），allow（白名单） |
|**domain**|String|域名 |
|**cname**|String|为加速域名生成的一个CNAME域名，需要在域名解析服务商处将加速域名CNAME解析到该域名 |
|**archiveNo**|String|域名备案号 |
|**type**|String|域名加速类型，web表示图片及小文件加速 |
|**created**|String|创建时间 |
|**modified**|String|最后修改时间 |
|**status**|String|加速域名中国境内运行状态 ，online 表示启用；offline表示停用；configuring表示配置中；configure_failed表示配置失败 |
|**auditStatus**|String|域名审核状态，取值：0（未审核），1（审核通过），2（审核不通过） |
|**source**|[BackSourceInfo](getdomaindetail#backsourceinfo)| |
|**sourceType**|String|回源类型：取值 ips（IP列表），domain（域名）,oss（oss回源） |
|**defaultSourceHost**|String|默认的回源host|
|**backSourceType**|String|回源类型，只能为http（80端口回源）或者https（443端口回源），默认为http |
|**httpType**|String|http类型，只能为http或者https，默认为http。当设为https时，需要调用“设置通讯协议”接口上传证书和私钥 |
|**certificate**|String|用户证书，当Type为https时必须设置 |
|**rsaKey**|String|证书私钥 |
|**jumpType**|String|跳转类型，有三种类型：default、http、https |
|**certFrom**|String|证书来源，取值：ssl,defalut |
|**sslCertId**|String|证书id |
|**certName**|String|证书名称 |
|**certType**|String|证书类型 |
|**sslCertStartTime**|String|证书开始时间 |
|**sslCertEndTime**|String|证书结束时间 |
|**accelerateRegion**|String|加速区域|
|**txt**|String|txt记录|
|**overseaStatus**|Long|加速域名海外运行状态 (-1:不涉及海外加速,0:未激活,1:已激活,2:海外无该域名)|
### <div id="backsourceinfo">BackSourceInfo</div>
|名称|类型|描述|
|---|---|---|
|**ips**|[IpSourceInfo[]](getdomaindetail#ipsourceinfo)|ip回源配置，对应sourceType=ips的取值 |
|**domain**|[DomainSourceInfo[]](getdomaindetail#domainsourceinfo)|域名回源配置，对应sourceType=domain的取值 |
|**ossSource**|String|oss回源配置，对应sourceType=oss的取值 |
### <div id="domainsourceinfo">DomainSourceInfo</div>
|名称|类型|描述|
|---|---|---|
|**priority**|Integer|优先级（1-10）|
|**sourceHost**|String|自定义回源host，仅中国境内加速域名可配置|
|**domain**|String|回源域名|
### <div id="ipsourceinfo">IpSourceInfo</div>
|名称|类型|描述|
|---|---|---|
|**master**|Integer|1：主；2：备|
|**ip**|String|回源IP|
|**ratio**|Double|占比|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
