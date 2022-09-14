# 分布式数据库TiDB


## 简介
分布式数据库TiDB


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addWhiteListGroup**|POST|增加白名单分组。|
|**attachNetwork**|POST|当实例不欠费了或者续费了，开启TiDB实例的网络访问功能。|
|**createAccount**|POST|创建数据库账号，用户可以使用客户端，应用程序等通过该账号和密码登录数据库实例。|
|**createBackup**|POST|创建一个实例全量备份，可以对整个实例所有的数据库进行全量备份。同一时间点，只能有一个正在运行的备份任务|
|**createDataMigration**|POST|查询 TiDB 数据迁移任务的信息|
|**createInstance**|POST|创建一个TiDB实例|
|**createInstanceFromBackup**|POST|根据源实例全量备份创建一个新实例|
|**createReplication**|POST|创建一个TiCDC|
|**deleteBackup**|DELETE|删除TiDB的备份，仅允许删除用户生成的备份，系统自动备份不允许删除。|
|**deleteInstance**|DELETE|删除一个TiDB实例|
|**deleteInstanceByForce**|POST|强行删除TiDB 实例，包括包年包月未过期实例,仅用于运营后台接口|
|**deleteReplication**|DELETE|删除复制任务|
|**deleteWhiteListGroup**|DELETE|删除白名单分组。|
|**describeAccounts**|GET|查看某个实例下的账号信息|
|**describeAvailableZones**|GET|获取可用区|
|**describeBackupPolicy**|GET|查看实例当前的备份备份策略。|
|**describeBackups**|GET|查看该实例下所有备份的详细信息|
|**describeDataMigration**|GET|查询 TiDB 数据迁移任务的信息|
|**describeExposeType**|GET|查询k8s集群支持的集群外访问方式|
|**describeExternalAccessService**|GET|获取在混合云中TPaaS架构下从K8S集群外访问实例的地址|
|**describeInstanceAttributes**|GET|查询 TiDB 实例的详细信息|
|**describeInstanceClasses**|GET|规格获取接口|
|**describeInstances**|GET|查询实例列表|
|**describeInstancesTagValidity**|GET|检查资源是否可以打标|
|**describeNodes**|GET|获取某个实例下的节点信息|
|**describeOrderableInstanceType**|GET|获取当前用户售罄信息|
|**describeParameters**|GET|查看TiDB实例的配置参数|
|**describePodMap**|GET|获取某个实例下的所有节点对应的POD信息。|
|**describeReleases**|GET|查询实例Release列表|
|**describeReplications**|GET|查看TiCDC复制任务列表|
|**describeSSL**|GET|查询TiDB实例的ssl状态|
|**describeUpgradePlan**|GET|查询TiDB数据库的升级计划|
|**describeUpgradeVersions**|GET|获取TiDB数据库可升级到的版本|
|**describeVersions**|GET|获取TiDB产品提供的所有版本|
|**describeWhiteList**|GET|查看实例当前白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**detachNetwork**|POST|当实例欠费或者到期了，关闭TiDB实例的网络访问功能|
|**disableInternetAccess**|POST|关闭TiDB服务的公网访问域名|
|**disableSSL**|POST|关闭TiDB和MySQL客户端之间的SSL功能|
|**enableInternetAccess**|POST|开启TiDB服务的公网访问域名|
|**enableSSL**|POST|开启TiDB和MySQL客户端之间的SSL功能|
|**getInstanceReleaseName**|GET|查看实例对应的k8s中的releaseName【内部接口】|
|**modifyBackupPolicy**|POST|修改TiDB实例备份策略。|
|**modifyExternalAccessService**|POST|设置提供的Service的类型|
|**modifyInstanceName**|POST|修改实例名称，可支持中文，实例名的具体规则可参见帮助中心文档|
|**modifyInstanceSpec**|POST|修改实例规格，包含节点的水平扩容与垂直扩容|
|**modifyNodeNum**|POST|增加实例的节点数量。|
|**modifyParameters**|PUT|修改TiDB实例的配置参数。部分参数修改后，需要重启才能生效，具体可以参考PingCAP的相关文档|
|**modifyReplication**|POST|修改复制任务|
|**modifyWhiteList**|PUT|修改允许访问实例的IP白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**rebootPod**|POST|重启实例的pod|
|**resetPassword**|POST|创建数据库账号，用户可以使用客户端，应用程序等通过该账号和密码登录RDS数据库实例。|
|**resumeReplication**|POST|启动复制任务|
|**selectDetailList**|GET|根据实例的的id，获取实例相关信息,用于续费|
|**stopReplication**|POST|暂停复制任务|
|**testConnection**|POST|测试TiDB实例到复制目标的连通性|
|**upgradeEngineVersion**|POST|升级TiDB引擎版本，例如从4.0.6 升级到4.0.8. 目前支持小版本的升级，可升级到平台支持的最新的小版本|
|**verifyFilefromOSS**|POST|校验需要导入的备份文件在OSS上是否存在，需要的读取权限是否具备|
