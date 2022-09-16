# 分布式数据库TiDB


## 简介
分布式数据库TiDB


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addWhiteListGroup**|POST|增加白名单分组，用于用户管理不同类型或者来源的 IP 白名单。|
|**createAccount**|POST|创建数据库的高权限管理账号，用户可以使用客户端、应用程序等通过该账号和密码登录 TiDB 实例，然后通过SQL创建数据库和其他用户。一个数据库实例只能创建一个高权限账号。|
|**createBackup**|POST|进行 TiDB 实例的全量备份，对实例中所有的数据库进行备份。同一时间，只能有一个正在运行的备份任务。|
|**createDataMigration**|POST|创建一个数据迁移任务，可以将对象存储 OSS 中的数据导入到 TiDB 实例中，具体可以参考帮助文档。|
|**createInstance**|POST|创建一个 TiDB 实例。创建时需要指定 TiDB 各类节点的数目，规格，存储空间等。 TiFlash和TiCDC节点在创建时不是必须的，可以在需要时，通过扩容的功能创建TiFlash和TiCDC节点。|
|**createInstanceFromBackup**|POST|创建一个新的 TiDB 实例，并将指定的备份恢复到该实例上。|
|**createReplication**|POST|创建一个数据复制任务，可以将 TiDB 的增量数据同步到下游的 MySQL， TiDB 或者 Kafka 中。|
|**deleteBackup**|DELETE|删除TiDB的备份，仅允许删除用户创建的备份，系统的自动备份不允许删除。|
|**deleteInstance**|DELETE|删除指定的 TiDB 实例。实例删除后，数据不可恢复，请谨慎使用。|
|**deleteReplication**|DELETE|删除指定的复制任务。|
|**deleteWhiteListGroup**|DELETE|删除指定的白名单分组。|
|**describeAccounts**|GET|查看当前实例下的账号信息。|
|**describeAvailableZones**|GET|查询指定地域下可以提供 TiDB 服务的可用区。|
|**describeBackupPolicy**|GET|查看实例当前的备份策略。|
|**describeBackups**|GET|查看该实例下所有备份的详细信息|
|**describeDataMigration**|GET|查询 TiDB 数据迁移任务的详细信息，例如任务的开始、完成时间，任务状态等等。|
|**describeInstanceAttributes**|GET|查询 TiDB 实例的详细信息，例如TiDB的具体版本号，各个节点的规格、存储空间以及连接信息等等。|
|**describeInstanceClasses**|GET|获取各种 TiDB 节点支持的具体规格。|
|**describeInstances**|POST|查询当前账号下所有的 TiDB 实例。|
|**describeNodes**|GET|获取某个实例下的所有节点的主要性能信息，如CPU，内存，存储空间等。 该性能信息从云监控获取，为上一个监控周期的数据。|
|**describeOrderableInstanceType**|GET|获取当前用户售罄信息。|
|**describeParameters**|GET|查看TiDB实例的主要配置参数。|
|**describeReplications**|GET|查询当前实例下所有的复制任务。|
|**describeSSL**|GET|查询 TiDB 实例的 SSL 的开启状态。|
|**describeUpgradePlan**|GET|查询当前 TiDB 实例的升级计划。|
|**describeUpgradeVersions**|GET|获取当前 TiDB 实例可升级到的目标版本。|
|**describeVersions**|GET|查询 TiDB 服务支持的数据库版本。|
|**describeWhiteList**|GET|查看实例当前白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**disableInternetAccess**|POST|关闭 TiDB 实例的 Internet 公网服务。 关闭后，将不能在 VPC 外访问 TiDB 实例。|
|**disableSSL**|POST|关闭 TiDB 和 MySQL 客户端之间的 SSL 连接功能。|
|**enableInternetAccess**|POST|开启 TiDB 实例的 Internet 公网服务。开启后，并配置 IP 白名单后，可以在 VPC 外通过公网域名访问 TiDB 实例。|
|**enableSSL**|POST|开启 TiDB 和 MySQL 客户端之间的 SSL 连接功能。|
|**modifyBackupPolicy**|POST|修改 TiDB 实例备份策略，例如全量备份的日期，时间等。|
|**modifyInstanceName**|POST|修改实例名称，可支持中文，实例名的具体规则可参见帮助中心文档。|
|**modifyInstanceSpec**|POST|修改 TiDB 实例中各类节点中的数目与规格。支持 TiDB 节点和 Monitor 节点数目和规格的同时调整。 如果当前实例无 TiFlash 和 TiCDC 节点，那么在增加 TiFlash 和 TiCDC 节点数目时，可同时指定其规格。|
|**modifyNodeNum**|POST|修改 TiDB 实例中各类节点的数量。如果当前实例无TiFlash和TiCDC节点，那么在增加TiFlash和TiCDC节点数目时，可同时指定其规格。|
|**modifyParameters**|PUT|修改TiDB实例的配置参数。部分参数修改后，需要重启才能生效，具体可以参考PingCAP的相关文档。|
|**modifyReplication**|POST|修改复制任务，修改前需要先暂停复制任务。为保证复制任务的可靠性，目前仅允许修改部分配置。|
|**modifyWhiteList**|PUT|修改允许访问实例的IP白名单。白名单是允许访问当前实例的IP/IP段列表，缺省情况下，白名单对本VPC开放。如果用户开启了外网访问的功能，还需要对外网的IP配置白名单。|
|**rebootPod**|POST|重启实例的某类节点。重启采用滚动重启的方式，如果该类节点有多个，通常不会中断实例的服务。|
|**resetPassword**|POST|重置 TiDB 实例的高权限账号的密码。|
|**resumeReplication**|POST|继续暂停的复制任务。|
|**stopReplication**|POST|暂停指定的复制任务。注意：如果暂停的时间过长，会导致 TiCDC 节点的磁盘空间写满，导致复制任务错误或失败。|
|**upgradeEngineVersion**|POST|升级TiDB引擎版本，例如从4.0.8 升级到 5.4.0等。|
|**verifyFilefromOSS**|POST|校验需要导入的备份文件在OSS上是否存在，需要的读取权限是否具备。|
