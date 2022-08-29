# 从 ClickHouse 迁移

本文主要介绍如何从 ClickHouse 将数据库表及数据迁移到 Starwift 上。

### 前提条件
数据迁移前，请首先确认源 ClickHouse 实例与目标实例 Starwift 之间网络是否畅通。

- 源实例是云数据库 ClickHouse 或者自建的 ClickHouse，目标实例是 Starwift，且在同一个VPC内，可以直接使用remote函数进行迁移。
- 如果无法进行网络连通操作，建议在源实例将数据导出为文件，然后通过 clickhouse-client 客户端将文件导入到目标实例云数据库ClickHouse。
- 如果无法进行网络连通操作，但是已经有了Spark、Flink等基础设施，也可以尝试编写Spark、Flink job将源实例数据读出，然后写入目标实例云数据库ClickHouse。

### 一. 结构迁移
根据操作系统类型及源 ClickHouse 版本下载对应的客户端。下载链接，请参见 [clickhouse-client](https://clickhouse.com/docs/zh/getting-started/install/?spm=a2c4g.11186623.0.0.2156f3daJywCnC#install-from-deb-packages) 。

#### 1. 查看源实例的database列表
```
clickhouse-client --host="<old host>" --port="<old port>" --user="<old user name>" --password="<old password>" --query="SHOW databases"  > database.list
```

**参数说明**

| 参数          | 说明                         |
| ------------- | :--------------------------- |
| old host      | 源实例的地址。               |
| old port      | 源实例的端口号。             |
| old user name | 源实例创建的数据库账号。     |
| old password  | 源实例数据库账号对应的密码。 |

> **说明** ：
>
> system是系统数据库，不需要迁移，可以直接过滤掉。

#### 2.查看源实例的table列表
```
clickhouse-client --host="<old host>" --port="<old port>" --user="<old user name>" --password="<old password>" --query="SHOW tables from <database_name>"  > table.list
```

<database_name>表示希望查看的database。其他参数描述可参见“步骤1：查看源实例的database列表“。

可以通过系统表直接查询所有database、table名称。
```
select distinct database, name from system.tables where database != 'system';
```

> **说明** 
>
> 查询到的表名中，如果有以.inner.开头的表，则它们是物化视图的内部表示，不需要迁移，可以直接过滤掉。

#### 3. 导出源实例的建表DDL
```
clickhouse-client --host="<old host>" --port="<old port>" --user="<old user name>" --password="<old password>" --query="SHOW CREATE TABLE <database_name>.<table_name>"  > table.sql
```

#### 4. 将建表DDL导入到目标实例 Starwift 中
```
clickhouse-client --host="<new host>" --port="<new port>" --user="<new user name>" --password="<new password>"  < table.sql
```

**参数说明**

| 参数          | 说明                                                   |
| ------------- | :----------------------------------------------------- |
| new host      | 目标实例分析型云数据库ClickHouse的地址。               |
| new port      | 目标实例分析型云数据库ClickHouse的端口号。             |
| new user name | 目标实例分析型云数据库ClickHouse的数据库账号。         |
| new password  | 目标实例分析型云数据库ClickHouse数据库账号对应的密码。 |


### 二. 数据迁移
- 如果源端为自建 ClickHouse，则可以跳过这一步。
- 如果源端为云数据库 ClickHouse，则需要将目标实例 Starwift 的网段加入到源实例的白名单中。可以在 Starwift 控制台查看其 VPC 网络，并且将该VPC的整个网段都加入到源实例的白名单中。

#### 方案一. 使用 remote 函数进行迁移
在目标实例 Starwift 中，通过如下SQL进行数据迁移。
```
insert into <new_database>.<new_table> select * from remote('old_endpoint', <old_database>.<old_table>, '<username>', '<password>');
```

**参数说明**

| 参数         | 说明                                                         |
| ------------ | :----------------------------------------------------------- |
| new_database | 目标实例分析型云数据库ClickHouse中的数据库名。               |
| new_table    | 目标实例分析型云数据库ClickHouse中的表名。                   |
| old_endpoint | 源实例的endpoint。此处要填写的是VPC内endpoint，而不是公网endpoint。 |
| old_database | 目标实例分析型云数据库ClickHouse数据库账号对应的密码。       |
| old_table    | 源实例的数据库名。                                           |
| username     | 源实例的表名。                                               |
| password     | 源实例的密码。                                               |



#### 方案二  通过文件导出导入方式进行数据迁移
以 CSV 文件格式为例：
1. 将数据从源实例数据库导出为CSV格式文件。
```
clickhouse-client --host="<old host>" --port="<oldport>" --user="<old user name>" --password="<old password>"  --query="select * from <database_name>.<table_name> FORMAT CSV"  > table.csv
```
2. 导入CSV文件到目标实例分析型云数据库ClickHouse。
```
clickhouse-client --host="<new host>" --port="<new port>" --user="<new user name>" --password="<new password>"  --query="insert into <database_name>.<table_name> FORMAT CSV"  < table.csv
```

#### 方案三. 通过Linux pipe管道进行流式导出导入

```
clickhouse-client --host="<old host>" --port="<old port>" --user="<user name>" --password="<password>"  --query="select * from <database_name>.<table_name> FORMAT CSV" | 
clickhouse-client --host="<new host>" --port="<new port>" --user="<user name>" --password="<password>"   --query="INSERT INTO <database_name>.<table_name> FORMAT CSV"
```
