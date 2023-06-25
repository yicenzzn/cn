# describeCacheInstances


## 描述
查询缓存Redis实例列表，可分页、可排序、可搜索、可过滤

## 请求方式
GET

## 请求地址
https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |缓存Redis实例所在区域的Region ID。目前有华北-北京、华南-广州、华东-上海三个区域，Region ID分别为cn-north-1、cn-south-1、cn-east-2|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |页码：取值范围[1,∞)，默认为1|
|**pageSize**|Integer|False| |分页大小：取值范围[10, 100]，默认为10|
|**filters**|[Filter[]](describecacheinstances#filter)|False| |过滤属性：<br>cacheInstanceId - 实例Id，精确匹配，可选择多个<br>cacheInstanceName - 实例名称，模糊匹配<br>cacheInstanceStatus - 实例状态，精确匹配，可选择多个(running：运行中，error：错误，creating：创建中，changing：变配中，configuring：参数修改中，restoring：备份恢复中，deleting：删除中)<br>redisVersion - redis引擎版本，精确匹配，可选择2.8和4.0<br>instanceType - 实例类型，精确匹配（redis表示主从版，redis_cluster表示集群版）<br>chargeMode - 计费类型，精确匹配（prepaid_by_duration表示包年包月预付费，postpaid_by_duration表示按配置后付费）<br>|
|**sorts**|[Sort[]](describecacheinstances#sort)|False| |排序属性：<br>createTime - 按创建时间排序(asc表示按时间正序，desc表示按时间倒序)<br>|
|**tagFilters**|[TagFilter[]](describecacheinstances#tagfilter)|False| |标签的过滤条件|
|**resourceGroupIds**|String[]|False| | |

### <div id="tagfilter">TagFilter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**values**|String[]|True| |Tag值|
### <div id="sort">Sort</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |排序条件的名称|
|**direction**|String|False| |排序条件的方向|
### <div id="filter">Filter</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describecacheinstances#result)|结果|
|**requestId**|String|本次请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**cacheInstances**|[CacheInstance[]](describecacheinstances#cacheinstance)|分页后的实例列表|
|**totalCount**|Integer|实例总数|
### <div id="cacheinstance">CacheInstance</div>
|名称|类型|描述|
|---|---|---|
|**cacheInstanceId**|String|实例ID|
|**cacheInstanceName**|String|实例名称|
|**cacheInstanceClass**|String|规格代码，2.8、4.0标准版是实例规格，4.0自定义分片集群版实例表示单分片规格|
|**cacheInstanceMemoryMB**|Integer|实例的总内存（MB），表示用户购买的可使用内存|
|**cacheInstanceStatus**|String|实例状态：creating表示创建中，running表示运行中，error表示错误，changing表示变更规格中，deleting表示删除中，configuring表示修改参数中，restoring表示备份恢复中，upgrading表示升级中|
|**cacheInstanceDescription**|String|实例描述|
|**createTime**|String|创建时间（ISO 8601标准的UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ）|
|**azId**|[AzId](describecacheinstances#azid)|az信息|
|**vpcId**|String|实例所属VPC ID|
|**subnetId**|String|实例所属子网ID|
|**connectionDomain**|String|实例的访问域名|
|**port**|Integer|实例的访问端口|
|**charge**|[Charge](describecacheinstances#charge)|实例的计费信息|
|**instanceVersion**|String|实例的详细版本号，形如x.x-x.x|
|**auth**|Boolean|连接实例时，是否需要密码认证，false表示无密码|
|**redisVersion**|String|创建实例时选择的引擎版本：目前支持2.8和4.0|
|**cacheInstanceType**|String|实例类型：master-slave（标准版）、cluster（代理集群版）、native-cluster（cluster集群版）|
|**ipv6On**|Integer|是否支持IPv6，0表示不支持（只能用IPv4），1表示支持|
|**tags**|[Tag[]](describecacheinstances#tag)|标签信息|
|**resourceGroupId**|String|实例所属资源组ID|
|**shardNumber**|Integer|实例分片数，标准版固定为1，自定义分片集群版实例分片数由用户创建时选择，其他实例为固定分片数|
|**memoryMBPerShard**|Integer|单分片内存大小（MB）|
|**otherDomains**|[InstanceDomain[]](describecacheinstances#instancedomain)|实例其他访问域名列表|
|**slaveAppendonly**|String|从节点aof开关|
|**databaseNum**|String|db数量|
|**maxmemoryPolicy**|String|淘汰策略|
|**replicaNumber**|Integer|副本数，含主副本|
|**enableSmartProxy**|Integer|实例是否开启SmartProxy，当架构类型为native-cluster时才有效，1表示开启，0表示不开启|
|**cpuArchType**|String|cpu架构类型:arm64、amd64|
### <div id="instancedomain">InstanceDomain</div>
|名称|类型|描述|
|---|---|---|
|**domainName**|String|域名|
### <div id="tag">Tag</div>
|名称|类型|描述|
|---|---|---|
|**key**|String|标签的键|
|**value**|String|标签的值|
### <div id="charge">Charge</div>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
### <div id="azid">AzId</div>
|名称|类型|描述|
|---|---|---|
|**azSpecifyType**|String|AZ指定方式，SpecifyByReplicaGroup表示按副本组指定，SpecifyByCluster表示按整个集群指定|
|**azsForCluster**|String[]|为集群指定的AZ范围，按集群指定AZ时生效|
|**master**|String|缓存Redis主实例所在区域的可用区ID，按副本组指定AZ时生效|
|**slave**|String|缓存Redis从实例所在区域的可用区ID，按副本组指定AZ时生效|

## 返回码
|HTTP状态码|错误码|描述|
|---|---|---|
|**200**||OK|

## 请求示例
GET
```
@Test
public void testGetInstanceList() {
  // 1. 设置请求参数
  Filter redisVersionFilter = new Filter(); // 过滤条件：4.0版本
  redisVersionFilter.name("redisVersion").operator("eq").addValue("4.0");
  Filter redisTypeFilter = new Filter(); // 过滤条件：集群版
  redisTypeFilter.name("instanceType").operator("eq").addValue("redis_cluster");
  List<Filter> filters = new ArrayList<>(); // 多个条件是并且的关系
  filters.add(redisVersionFilter);
  filters.add(redisTypeFilter);

  List<Sort> sorts = new ArrayList<>(); // 排序：按创建时间降序
  sorts.add(new Sort().name("createTime").direction("desc"));

  DescribeCacheInstancesRequest request = new DescribeCacheInstancesRequest();
  request.regionId("cn-north-1").filters(filters).sorts(sorts).pageNumber(1).pageSize(20); // 取第一页，一页20个实例

  // 2. 发起请求
  DescribeCacheInstancesResponse response = redisClient.describeCacheInstances(request);

  // 3. 处理响应结果
  System.out.println(new Gson().toJson(response));
}

```

## 返回示例
```
{
    "requestId": "c3o559jq7qbwwfm9qngbsr7jm99h5mc2", 
    "result": {
        "cacheInstances": [
            {
                "auth": true, 
                "azId": {
                    "master": "cn-north-1a", 
                    "slave": "cn-north-1b"
                }, 
                "cacheInstanceClass": "redis.m.micro.basic", 
                "cacheInstanceDescription": "", 
                "cacheInstanceId": "redis-dr8kqlkauchk", 
                "cacheInstanceMemoryMB": 1024, 
                "cacheInstanceName": "测试", 
                "cacheInstanceStatus": "running", 
                "cacheInstanceType": "master-slave", 
                "charge": {
                    "chargeMode": "postpaid_by_duration", 
                    "chargeStartTime": "2021-07-05T02:44:34Z", 
                    "chargeStatus": "normal"
                }, 
                "connectionDomain": "redis-dr8kqlkauchk-proxy-nlb.jvessel-open-hb.jdcloud.com", 
                "createTime": "2021-07-05T02:43:43Z", 
                "instanceVersion": "4.0-1.3", 
                "ipv6On": 0, 
                "memoryMBPerShard": 1024, 
                "port": 6379, 
                "redisVersion": "4.0", 
                "shardNumber": 1, 
                "subnetId": "subnet-mvge5y02rx", 
                "tags": [
                    {
                        "key": "部门", 
                        "value": "研发部"
                    }
                ], 
                "vpcId": "vpc-6nz3a9drut"
            }
        ], 
        "totalCount": 1
    }
}
```
